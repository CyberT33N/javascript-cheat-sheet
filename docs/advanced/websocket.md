# Websocket

# Pattern

## 1. WebSocket Connection Pooling

**Concept:**  Manage a limited set of connections that can be shared across your application, rather than creating new connections for each component.  Reduces server load and improves performance.

**Example (JavaScript):**

```javascript
class WebSocketConnectionPool {
  constructor(serverUrl, poolSize = 3) {
    this.serverUrl = serverUrl;
    this.poolSize = poolSize;
    this.connections = [];
    this.connectionIndex = 0;
    this.initialize();
  }

  initialize() {
    for (let i = 0; i < this.poolSize; i++) {
      this.createConnection();
    }
  }

  createConnection() {
    const ws = new WebSocket(this.serverUrl);

    ws.onopen = () => {
      console.log(`Connection ${this.connections.length} established`);
    };

    ws.onerror = (error) => {
      console.error('WebSocket error:', error);
      // Handle reconnection
      this.handleReconnection(this.connections.indexOf(ws));
    };

    this.connections.push(ws);
    return ws;
  }

  getConnection() {
    // Simple round-robin selection
    const connection = this.connections[this.connectionIndex];
    this.connectionIndex = (this.connectionIndex + 1) % this.poolSize;
    return connection;
  }

  handleReconnection(index) {
    setTimeout(() => {
      if (index >= 0 && index < this.connections.length) {
        this.connections[index] = this.createConnection();
      }
    }, 1000);
  }

  sendMessage(message) {
    const connection = this.getConnection();
    if (connection.readyState === WebSocket.OPEN) {
      connection.send(JSON.stringify(message));
      return true;
    }
    return false;
  }
}

// Usage
const pool = new WebSocketConnectionPool("ws://your-websocket-server");
pool.sendMessage({ type: "data", payload: "Hello!" });
```

## 2. Heartbeat Mechanisms

**Concept:** Send regular "ping" messages to verify the connection is alive and functioning properly.  Detects and handles "zombie" connections.

**Example (JavaScript):**

```javascript
class HeartbeatWebSocket {
  constructor(url, heartbeatInterval = 30000) {
    this.url = url;
    this.heartbeatInterval = heartbeatInterval;
    this.connection = null;
    this.heartbeatTimer = null;
    this.connect();
  }

  connect() {
    this.connection = new WebSocket(this.url);

    this.connection.onopen = () => {
      console.log('Connection established');
      this.startHeartbeat();
    };

    this.connection.onclose = () => {
      console.log('Connection closed');
      this.stopHeartbeat();
      // Reconnect logic would go here
    };

    this.connection.onmessage = (event) => {
      const message = JSON.parse(event.data);
      if (message.type === 'pong') {
        // Reset heartbeat timer on pong
        this.resetHeartbeat();
      } else {
        // Handle regular messages
        this.handleMessage(message);
      }
    };
  }

  startHeartbeat() {
    this.heartbeatTimer = setInterval(() => {
      if (this.connection.readyState === WebSocket.OPEN) {
        this.connection.send(JSON.stringify({ type: 'ping' }));

        // Set a timeout to detect missed pongs
        this.pongTimeoutTimer = setTimeout(() => {
          console.log('Pong not received, connection may be dead');
          this.connection.close();
        }, 5000);
      }
    }, this.heartbeatInterval);
  }

  resetHeartbeat() {
    if (this.pongTimeoutTimer) {
      clearTimeout(this.pongTimeoutTimer);
      this.pongTimeoutTimer = null;
    }
  }

  stopHeartbeat() {
    if (this.heartbeatTimer) {
      clearInterval(this.heartbeatTimer);
      this.heartbeatTimer = null;
    }
    this.resetHeartbeat();
  }

  handleMessage(message) {
    // Process regular application messages
    console.log('Received message:', message);
  }

  send(message) {
    if (this.connection.readyState === WebSocket.OPEN) {
      this.connection.send(JSON.stringify(message));
    }
  }
}
```

## 3. Reconnection Strategies

**Concept:**  Automatically attempt to reconnect when a connection is lost.  Use exponential backoff to avoid overwhelming the server.

**Example (JavaScript):**

```javascript
class ReconnectingWebSocket {
  constructor(url, options = {}) {
    this.url = url;
    this.options = {
      maxReconnectAttempts: 10,
      reconnectInterval: 1000,
      maxReconnectInterval: 30000,
      reconnectDecay: 1.5,
      ...options
    };

    this.reconnectAttempts = 0;
    this.socket = null;
    this.isConnecting = false;
    this.messageQueue = [];

    this.connect();
  }

  connect() {
    if (this.isConnecting) return;

    this.isConnecting = true;
    this.socket = new WebSocket(this.url);

    this.socket.onopen = () => {
      console.log('Connection established');
      this.isConnecting = false;
      this.reconnectAttempts = 0;

      // Send any queued messages
      while (this.messageQueue.length > 0) {
        const message = this.messageQueue.shift();
        this.send(message);
      }

      if (this.onopen) this.onopen();
    };

    this.socket.onclose = (event) => {
      if (!event.wasClean) {
        this.attemptReconnect();
      }

      if (this.onclose) this.onclose(event);
    };

    this.socket.onerror = (error) => {
      console.error('WebSocket error:', error);
      this.socket.close();

      if (this.onerror) this.onerror(error);
    };

    this.socket.onmessage = (event) => {
      if (this.onmessage) this.onmessage(event);
    };
  }

  attemptReconnect() {
    if (this.reconnectAttempts >= this.options.maxReconnectAttempts) {
      console.log('Max reconnect attempts reached');
      return;
    }

    const delay = Math.min(
      this.options.reconnectInterval * Math.pow(this.options.reconnectDecay, this.reconnectAttempts),
      this.options.maxReconnectInterval
    );

    this.reconnectAttempts++;
    console.log(`Reconnecting in ${delay}ms... (Attempt ${this.reconnectAttempts})`);

    setTimeout(() => {
      this.isConnecting = false;
      this.connect();
    }, delay);
  }

  send(message) {
    if (this.socket && this.socket.readyState === WebSocket.OPEN) {
      this.socket.send(typeof message === 'string' ? message : JSON.stringify(message));
      return true;
    } else {
      this.messageQueue.push(message);
      return false;
    }
  }

  close() {
    if (this.socket) {
      this.socket.close();
    }
  }
}
```

## 4. Message Queuing

**Concept:** Store outgoing messages during disconnection periods and send them once the connection is restored.  Prevents data loss.

**Example (JavaScript):**

```javascript
class QueuedWebSocket {
  constructor(url) {
    this.url = url;
    this.socket = null;
    this.queue = [];
    this.connected = false;
    this.maxQueueSize = 100;
    this.connect();
  }

  connect() {
    this.socket = new WebSocket(this.url);

    this.socket.onopen = () => {
      console.log('Connection established');
      this.connected = true;
      this.flushQueue();
    };

    this.socket.onclose = () => {
      console.log('Connection closed');
      this.connected = false;
      // Reconnection logic would go here
    };

    this.socket.onerror = (error) => {
      console.error('WebSocket error:', error);
    };

    this.socket.onmessage = (event) => {
      // Handle incoming messages
      this.handleMessage(JSON.parse(event.data));
    };
  }

  send(message) {
    const messageObject = {
      id: this.generateId(),
      timestamp: Date.now(),
      content: message,
      attempts: 0
    };

    if (this.connected && this.socket.readyState === WebSocket.OPEN) {
      this.sendMessage(messageObject);
    } else {
      this.enqueueMessage(messageObject);
    }
  }

  sendMessage(messageObject) {
    messageObject.attempts++;
    try {
      this.socket.send(JSON.stringify(messageObject.content));
      return true;
    } catch (error) {
      console.error('Failed to send message:', error);
      this.enqueueMessage(messageObject);
      return false;
    }
  }

  enqueueMessage(messageObject) {
    // Keep queue size manageable
    if (this.queue.length >= this.maxQueueSize) {
      this.queue.shift(); // Remove oldest message
    }
    this.queue.push(messageObject);
  }

  flushQueue() {
    if (!this.connected) return;

    const queueCopy = [...this.queue];
    this.queue = [];

    queueCopy.forEach(messageObject => {
      if (!this.sendMessage(messageObject)) {
        // If sending fails, it will be re-enqueued
      }
    });
  }

  handleMessage(message) {
    console.log('Received message:', message);
    // Process incoming message
  }

  generateId() {
    return Math.random().toString(36).substring(2, 15);
  }
}
```

## 5. Protocol Definition

**Concept:**  Define a structured message protocol to ensure clients and servers understand each other.  Improves maintainability and reduces errors.

**Example (JavaScript):**

```javascript
// Protocol Definition
const MessageTypes = {
  AUTHENTICATION: 'auth',
  EVENT: 'event',
  COMMAND: 'command',
  QUERY: 'query',
  RESPONSE: 'response',
  ERROR: 'error'
};

class WebSocketProtocol {
  constructor(url) {
    this.url = url;
    this.socket = null;
    this.messageHandlers = {};
    this.pendingRequests = new Map();
    this.requestTimeout = 10000; // 10 seconds
    this.connect();
  }

  connect() {
    this.socket = new WebSocket(this.url);

    this.socket.onopen = () => {
      console.log('Connection established');
    };

    this.socket.onmessage = (event) => {
      try {
        const message = JSON.parse(event.data);
        this.handleMessage(message);
      } catch (error) {
        console.error('Failed to parse message:', error);
      }
    };

    this.socket.onclose = () => {
      console.log('Connection closed');
    };

    this.socket.onerror = (error) => {
      console.error('WebSocket error:', error);
    };
  }

  handleMessage(message) {
    // Validate message format
    if (!message.type || !message.id) {
      console.error('Invalid message format:', message);
      return;
    }

    // Handle responses to requests
    if (message.type === MessageTypes.RESPONSE && this.pendingRequests.has(message.requestId)) {
      const { resolve } = this.pendingRequests.get(message.requestId);
      resolve(message.payload);
      this.pendingRequests.delete(message.requestId);
      return;
    }

    // Handle errors
    if (message.type === MessageTypes.ERROR && this.pendingRequests.has(message.requestId)) {
      const { reject } = this.pendingRequests.get(message.requestId);
      reject(new Error(message.error));
      this.pendingRequests.delete(message.requestId);
      return;
    }

    // Handle other message types
    if (this.messageHandlers[message.type]) {
      this.messageHandlers[message.type](message.payload, message);
    } else {
      console.warn('No handler for message type:', message.type);
    }
  }

  sendMessage(type, payload, requestId = null) {
    if (this.socket.readyState !== WebSocket.OPEN) {
      return Promise.reject(new Error('WebSocket is not connected'));
    }

    const id = this.generateId();
    const message = {
      id,
      type,
      timestamp: Date.now(),
      payload
    };

    if (requestId) {
      message.requestId = requestId;
    }

    this.socket.send(JSON.stringify(message));

    // If this is a query that expects a response, return a promise
    if (type === MessageTypes.QUERY) {
      return new Promise((resolve, reject) => {
        this.pendingRequests.set(id, { resolve, reject });

        // Set timeout for the request
        setTimeout(() => {
          if (this.pendingRequests.has(id)) {
            this.pendingRequests.delete(id);
            reject(new Error('Request timed out'));
          }
        }, this.requestTimeout);
      });
    }

    return Promise.resolve();
  }

  on(messageType, handler) {
    this.messageHandlers[messageType] = handler;
  }

  authenticate(credentials) {
    return this.sendMessage(MessageTypes.AUTHENTICATION, credentials);
  }

  query(resource, parameters = {}) {
    return this.sendMessage(MessageTypes.QUERY, { resource, parameters });
  }

  command(action, parameters = {}) {
    return this.sendMessage(MessageTypes.COMMAND, { action, parameters });
  }

  publishEvent(event, data = {}) {
    return this.sendMessage(MessageTypes.EVENT, { event, data });
  }

  generateId() {
    return Math.random().toString(36).substring(2, 15);
  }
}
```

## 6. Channel Subscriptions

**Concept:**  Allow clients to receive only the data they need by subscribing to specific channels. Reduces bandwidth usage and processing overhead.

**Example (JavaScript):**

```javascript
class ChannelWebSocket {
  constructor(url) {
    this.url = url;
    this.socket = null;
    this.subscriptions = new Map();
    this.reconnectAttempts = 0;
    this.maxReconnectAttempts = 10;
    this.connect();
  }

  connect() {
    this.socket = new WebSocket(this.url);

    this.socket.onopen = () => {
      console.log('Connection established');
      this.reconnectAttempts = 0;

      // Resubscribe to all channels after reconnection
      for (const [channel, callback] of this.subscriptions.entries()) {
        this.sendSubscription(channel);
      }
    };

    this.socket.onmessage = (event) => {
      try {
        const message = JSON.parse(event.data);
        this.handleMessage(message);
      } catch (error) {
        console.error('Failed to parse message:', error);
      }
    };

    this.socket.onclose = () => {
      console.log('Connection closed');
      if (this.reconnectAttempts < this.maxReconnectAttempts) {
        this.reconnectAttempts++;
        const delay = Math.min(1000 * Math.pow(1.5, this.reconnectAttempts), 30000);
        setTimeout(() => this.connect(), delay);
      }
    };

    this.socket.onerror = (error) => {
      console.error('WebSocket error:', error);
    };
  }

  handleMessage(message) {
    if (!message.channel || !message.data) {
      console.warn('Received malformed message:', message);
      return;
    }

    // Forward message to subscribers
    if (this.subscriptions.has(message.channel)) {
      const callback = this.subscriptions.get(message.channel);
      callback(message.data);
    }

    // Handle system messages
    if (message.channel === 'system') {
      this.handleSystemMessage(message.data);
    }
  }

  handleSystemMessage(data) {
    if (data.type === 'subscription_confirm') {
      console.log(`Subscription to ${data.channel} confirmed`);
    } else if (data.type === 'error') {
      console.error('System error:', data.message);
    }
  }

  subscribe(channel, callback) {
    if (typeof callback !== 'function') {
      throw new Error('Callback must be a function');
    }

    this.subscriptions.set(channel, callback);

    if (this.socket.readyState === WebSocket.OPEN) {
      this.sendSubscription(channel);
    }

    return {
      unsubscribe: () => this.unsubscribe(channel)
    };
  }

  unsubscribe(channel) {
    if (!this.subscriptions.has(channel)) {
      return false;
    }

    this.subscriptions.delete(channel);

    if (this.socket.readyState === WebSocket.OPEN) {
      this.socket.send(JSON.stringify({
        action: 'unsubscribe',
        channel
      }));
    }

    return true;
  }

  sendSubscription(channel) {
    this.socket.send(JSON.stringify({
      action: 'subscribe',
      channel
    }));
  }

  publish(channel, data) {
    if (this.socket.readyState !== WebSocket.OPEN) {
      return false;
    }

    this.socket.send(JSON.stringify({
      action: 'publish',
      channel,
      data
    }));

    return true;
  }
}
```

## Scaling WebSockets

*   **Horizontal Scaling:** Use load balancers (NGINX, HAProxy) with WebSocket support.
*   **Message Broadcasting:**  Use Redis or similar pub/sub systems to distribute messages across multiple server instances.

**Example NGINX Configuration:**

```nginx
upstream websocket_servers {
    hash $remote_addr consistent;
    server backend1.example.com:8080;
    server backend2.example.com:8080;
    server backend3.example.com:8080;
}

server {
    listen 80;
    server_name ws.example.com;

    location /ws/ {
        proxy_pass http://websocket_servers;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_read_timeout 3600s;
        proxy_send_timeout 3600s;
    }
}
```

**Example Node.js with Redis:**

```javascript
const WebSocket = require('ws');
const Redis = require('ioredis');
const http = require('http');

// Create Redis clients
const subscriber = new Redis();
const publisher = new Redis();

// Create HTTP server
const server = http.createServer();

// Create WebSocket server
const wss = new WebSocket.Server({ server });

// Store connected clients and their subscriptions
const clients = new Map();

wss.on('connection', (ws) => {
  const clientId = generateId();
  const clientData = {
    id: clientId,
    subscriptions: new Set()
  };

  clients.set(ws, clientData);

  console.log(`Client ${clientId} connected`);

  ws.on('message', (message) => {
    try {
      const data = JSON.parse(message);

      switch (data.action) {
        case 'subscribe':
          handleSubscribe(ws, clientData, data.channel);
          break;
        case 'unsubscribe':
          handleUnsubscribe(ws, clientData, data.channel);
          break;
        case 'publish':
          handlePublish(data.channel, data.data);
          break;
        default:
          console.warn(`Unknown action: ${data.action}`);
      }
    } catch (error) {
      console.error('Error processing message:', error);
    }
  });

  ws.on('close', () => {
    // Clean up subscriptions
    clientData.subscriptions.forEach(channel => {
      subscriber.unsubscribe(channel);
    });

    clients.delete(ws);
    console.log(`Client ${clientId} disconnected`);
  });
});

// Handle subscribe action
function handleSubscribe(ws, clientData, channel) {
  // Subscribe to Redis channel
  subscriber.subscribe(channel);

  // Add to client's subscriptions
  clientData.subscriptions.add(channel);

  // Confirm subscription
  ws.send(JSON.stringify({
    channel: 'system',
    data: {
      type: 'subscription_confirm',
      channel
    }
  }));
}

// Handle unsubscribe action
function handleUnsubscribe(ws, clientData, channel) {
  // Remove from client's subscriptions
  clientData.subscriptions.delete(channel);

  // Check if we need to unsubscribe from Redis
  let hasOtherSubscribers = false;
  clients.forEach(client => {
    if (client.subscriptions.has(channel)) {
      hasOtherSubscribers = true;
    }
  });

  if (!hasOtherSubscribers) {
    subscriber.unsubscribe(channel);
  }
}

// Handle publish action
function handlePublish(channel, data) {
  // Publish to Redis
  publisher.publish(channel, JSON.stringify(data));
}

// Process messages from Redis
subscriber.on('message', (channel, message) => {
  // Broadcast to all clients subscribed to this channel
  clients.forEach((clientData, ws) => {
    if (clientData.subscriptions.has(channel) && ws.readyState === WebSocket.OPEN) {
      ws.send(JSON.stringify({
        channel,
        data: JSON.parse(message)
      }));
    }
  });
});

function generateId() {
  return Math.random().toString(36).substring(2, 15);
}

// Start server
const PORT = process.env.PORT || 8080;
server.listen(PORT, () => {
  console.log(`WebSocket server listening on port ${PORT}`);
});
```
