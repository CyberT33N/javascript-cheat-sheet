# Classes

```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  play(length) {
    console.log(`${this.name} is playing ${length} hours`);
  }

};

var leo = new Animal('Leo', 7);
console.log('leo name:' + leo.name);
console.log(leo.play(5));
```

<br><br>


# Change/add constructor value
```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  changeName(name, lastName) {
    this.name = name;
    this.lastName = lastName;
  }

};

var leo = new Animal('Leo', 7);
console.log('name before:' + leo.name);

leo.changeName('Peter', 'Doe');
console.log('name after:' + leo.name);
console.log('added last name:' + leo.lastName);
```



<br><br>


# static (isolated function)
```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  static getDetails(){
    const r = 'API_results'; // do as example some api calls here
    return `Details about your pet: ${r}`;
  }

};

console.log('getDetails():' + Animal.getDetails());
```


<br><br>


# subclasses (inheritance)
```javascript
class Animal {

  constructor(name, energy){
    this.name = name;
    this.energy = energy;
  }

  getDetails(){
    return `${this.name} has ${this.energy} energy left` ;
  }

};

class Zoo extends Animal {
  /* 
    you can also remove the constructor and you are still able to access the sub class because we will use the subclass constructor in this case.

    If you want to use the parent class constructor your have to use super();
    https://www.w3schools.com/jsref/jsref_class_super.asp
  */
  constructor(name, energy, location){
    super(name, energy);
    this.location = location;
  }
};

var zooGermany = new Zoo('Leo', 1, 'Germany');
console.log(zooGermany);

// compared to es5 we can now use functions of the original constructor without manually inherit the object
var getDetails = zooGermany.getDetails();
console.log('getDetails: ' + getDetails);
```



<br><br>


# Multiple Inheritance (Mixins)


<br><br>
<br><br>

## TypeScript

<br><br>

### Example 1 - Default
- The helper function mix() extends from multiple classes and assign the this context to the instance of the parent class(ParentManager)
- ClassA contains a cunstructor which contains e.g. this.test which will be available aswell in ClassB


```typescript
type Constructor<T = {}> = new (...args: any[]) => T

export default function mix<T extends Constructor[]>(...bases: T) {
    class Base {
        [key: string]: any

        constructor(...args: any[]) {
            bases.forEach(base => {
                const instance = new base(...args)
                Object.assign(this, instance)
            })
        }
    }

    bases.forEach(base => {
        Object.getOwnPropertyNames(base.prototype).forEach(name => {
            Base.prototype[name] = base.prototype[name]
        })
    })

    return Base
}

export default class ParentManager extends mix(ClassA, ClassB) {
    constructor() {
        // will be passed to each extended Class. Please check example #2 for more control
        super('eth')
    }
}
```


## Example 2 - Custom nested properties for each extended class
- In comparsion to example 1 here we assign the instance of ClassB to this.balance. This is usefully when you want to create a more cleaner nested logic for better naming.
  - ClassB is still able to use this from ParentManager & ClassA
 
- MixinConfig:
  - property: The child property you want to use where you want to assign your instance at
  - initSuper: Set to true if you want to pass the arguments of super() from parent class to the class instance where you extend at. Default will be false
  - Class: The Class you want to extend from 
```typescript
// Type for constructor
type Constructor<T = {}> = new (...args: any[]) => T

// Type for mixin config
interface MixinConfig {
    Class: Constructor
    property?: string
    initSuper?: boolean
}

// Class mix function to combine multiple classes
export default function mix(...configs: MixinConfig[]) {
   class Base {
        [key: string]: any
     
        constructor(...args: any[]) {
            configs.forEach(config => {
                const { Class, property, initSuper } = config as MixinConfig

                // If initSuper is true, create new instance of the class with arguments from parent class
                const instance = initSuper ? new Class(...args) : new Class()

                if (property) {
                // Create new instance of the class at the custom property
                    this[property] = instance

                    // Assign this to the custom property from config
                    Object.assign(this, this[property])

                    /*
                    Assign this to the custom property from the class.
                    This is useful when the class has a method that uses this from parent class
                    */
                    Object.assign(this[property], this)
                } else {
                    // Create new instance of the class at the class itself if no custom property
                    Object.assign(this, instance)
                }
            })
        }
    }

    // Assign all methods from all classes to the Base class
    configs.forEach(config => {
        const { Class } = config

        Object.getOwnPropertyNames(Class.prototype).forEach(name => {
            Base.prototype[name] = Class.prototype[name]
        })
    })

    return Base as Constructor
}

export default class ParentManager extends mix(
    { Class: ClassA, initSuper: true  },
    { Class: ClassB, property: 'balance' }
) {
    [key: string]: ClassA & ClassB

    constructor() {
        super('eth')
    }
}
```


## Example 3 - Nested custom properties
- In comparsion to example #2 here you can e.g. acces this.classA.test() from this.classB.test()
```typescript
export default class EthCoinManager extends mix(
    // ==== THIRD PARTY ====
    { Class: EtherscanManager, property: 'etherscan' },
    { Class: CoinmarketCapManager, property: 'coinMarketCap' },

    // ==== LOGIC CLASSES ====
    { Class: CryptoAccountManager, initSuper: true },
    { Class: BalanceManager, property: 'balance' },
    { Class: TransactionManager, property: 'transaction' },

    // ==== UTILS ====
    { Class: Utils, property: 'utils' }
) {
    etherscan!: EtherscanManager
    coinMarketCap!: CoinmarketCapManager
    balance!: BalanceManager
    transaction!: TransactionManager

    constructor() {
        super('eth')
    }
}
```

```typescript
// Type for constructor
type Constructor<T = {}> = new (...args: any[]) => T

// Type for mixin config
interface MixinConfig {
    Class: Constructor
    property?: string,
    initSuper?: boolean
}

// Class mix function to combine multiple classes
export default function mix(...configs: MixinConfig[]) {
    class Base {
        [key: string]: any

        constructor(...args: any[]) {
            configs.forEach(config => {
                this.loadConfig(config, args)
            })
        }

        // Create new instance of the class from config
        getInstanceOfConfig(config: MixinConfig, args: any[]) {
            const { Class, initSuper } = config

            // If initSuper is true, create new instance of the class with arguments from parent class
            const instance = initSuper ? new Class(...args) : new Class()
            return instance
        }

        // Assign this to the instance
        getThisContextOfClass(config: MixinConfig, instance: object) {
            const { property } = config

            if (property) {
                // Create new instance of the class at the custom property
                this[property] = instance

                // Assign the custom property to parent class instance
                Object.assign(this, this[property])

                // Assign this to the custom property from the class.
                Object.assign(this[property], this)
            } else {
                // Create new instance of the class at the class itself if no custom property
                Object.assign(this, instance)
            }

            return this
        }

        // Assign all classes instances to custom property
        assignClassesToCustomProperty(customProperty: string, args: any[]) {
            configs.forEach(config => {
                const instance = this.getInstanceOfConfig(config, args)
                const thisContext = this.getThisContextOfClass(config, instance)
                Object.assign(this[customProperty], thisContext)
            })
        }

        // Load config and assign instance to parent class
        loadConfig(config: MixinConfig, args: any[]) {
            const instance = this.getInstanceOfConfig(config, args)

            // Assign this to the instance
            this.getThisContextOfClass(config, instance)

            const { property } = config

            // If custom property is set iterate over all classes and assign instances to the custom property
            if (property) {
                this.assignClassesToCustomProperty(property, args)
            } 
        }
    }

    // Assign all methods from all classes to the Base class
    configs.forEach(config => {
        const { Class } = config

        Object.getOwnPropertyNames(Class.prototype).forEach(name => {
            Base.prototype[name] = Class.prototype[name]
        })
    })

       return Base as Constructor<Base & 
        {
            [K in keyof Base]: Base[K]} &
            {[K in keyof InstanceType<MixinConfig['Class']>]: InstanceType<MixinConfig['Class']>[K]
        }>
}
```














<br><br>
<br><br>
<br><br>

## Common JS
```javascript
// ---- EXAMPLE #00 -----
class Class1 extends BaseClass {}
class Class2 extends BaseClass {}

class Example {
  class1: Class1 // Sorry for the Typescript
  class2: Class2

  constructor (props) {
    this.class1 = new Class1(props)
    this.class2 = new Class2(props)
  }
}




// ---- EXAMPLE #0 -----
/**
 * Multiple Inheritance by simply merging the props functions
 * together to be used as right side extension of the keyword "extends Classes.
 * Beware of the fact that order of classes matter, mpst outer right class
 * wins when methods with the same name collide. 
 * 
 * @param {Array<Object>} bases 
 */
function Classes(bases) {
    
    /**
     *  Merge and mix all functions
     *  @class
     */
    class Bases {

        /**
         * Calls the constructors of each class in the scope of Bases and adds it
         * to an instance of {@link Bases}
         */
        constructor(){
            bases.forEach(base => Object.assign(this, new base()))
        }
    }
    // combines the prototypes of each class passed
    bases.forEach(base => {
        Object.getOwnPropertyNames(base.prototype)
            .filter(prop => prop != 'constructor')
            .forEach(prop => Bases.prototype[prop] = base.prototype[prop])
    })
    return Bases
}

class A{
   sing(){console.log('lalilala')}
}

class B{
    speak(){console.log('hi all!')} 
}

class C extends Classes([A,B]){
    singAndSpeak(){
         this.sing()
         this.speak()
     }
}




// ---- EXAMPLE #1 -----
class Animal {
  constructor(){ 
    Object.assign(this, new Shark(), new Clock());
  };
};

class Shark {
  // only what's in constructor will be on the object, ence the weird this.bite = this.bite.
  constructor(){ this.color = "black"; this.bite = this.bite };
  bite(){ console.log("bite") };
  eat(){ console.log('eat') };
};

class Clock{
  constructor(){ this.tick = this.tick; };
  tick(){ console.log("tick"); };
};

let animal = new Animal();
animal.bite();
console.log(animal.color);
animal.tick();














// ---- EXAMPLE #2 (Real Mixin) -----
let MyMixin = (superclass) => class extends superclass {
  foo() {
    console.log('Name: ' + this.name);
  }
};

class MyBaseClass {
  constructor(){
  this.name = 'Laura'
  }
}

class MyClass extends MyMixin(MyBaseClass) {
  /* ... */
}


let c = new MyClass();
c.foo(); // prints "foo from MyMixin"
```


<br><br>

# Use always same instance (singleton)

<br><br>


### Example #1
```
class ModelManager {
    // eslint-disable-next-line no-use-before-define
    private static instance: ModelManager
    models: Array<{
        modelName: string
        model: mongoose.Model<any>
    }>

    private constructor() {
        this.models = []
    }
  
    static async getInstance() {
        if (this.instance) {
            return this.instance
        }
      
        // Create instance
        this.instance = new ModelManager()

        // ==== VARIABLES ====
        this.instance.models = []

        // ==== INITIALIZATION ====
        await this.instance.init()

        return this.instance
    }

    private async init() {
        if(!this.models) {
            const path = `${getDirname()}/**/*.model.js`
            this.models = await this.globModels(path)
        }
    }

    private async globModels(expression: string) {
        const modelPaths = await glob(expression)
 
        const models = []

        for (const path of modelPaths) {
            const file = await import(path)
            const Model = await file.default()
            models.push(Model)
        }

        return models
    }

    public async getModels() {
        const models = this.models
        return models
    }

    public async getModel(name: string) {
        const model = this.models.find(model => model.modelName === name)
        return model
    }
}
```
- This is how you can reset the instance in your test:
	```typescript
	beforeEach(async() => {
		// Reset instance before creating a new one
		(<any>ModelManager).instance = null
		
		initStub = sinon.stub(
		    ModelManager.prototype, 'init' as keyof ModelManager
		).resolves()
		
		modelManager = await ModelManager.getInstance()
	})
	```



### Example #2
- old style cjs
```javascript
/**
 *
 */
class MongooseUtils {
    /**
     *
     * @param name
     * @returns {MongooseUtils}
     */
    constructor(name) {
        if (MongooseUtils.instance === undefined) {
            // Because we override here the instance of the class with this we can declear any first singleton init call properties here with this.
            this.base = 1234
            MongooseUtils.instance = this
        }

        // If you want to change instance properties by inherit a new instance class with properties you must override the instance which we return. If you create a new instance and do not pass params for consstructor then we will use a fallback to the last value of the singleton
        MongooseUtils.instance.name = name || MongooseUtils.instance.name

        return MongooseUtils.instance
    }

    /**
     *
     * @param data
     */
    createData(data){
        this.example = data
    }
}

const instanceA = new MongooseUtils('test1')
instanceA.createData('a')
console.log('instanceA: ' + instanceA.example) // <-- will print a
console.log('instanceA name: ' + instanceA.name) // <-- will print test1
console.log('instanceA base: ' + instanceA.base) // <-- will print 1234

const instance2 = new MongooseUtils()
console.log('instance2: ' + instance2.example) // <-- will print a
console.log('instance2 name: ' + instance2.name) // <-- will print test1
console.log('instance2 base: ' + instance2.base) // <-- will print 1234

const instance3 = new MongooseUtils('test3')
console.log('instance3: ' + instance3.example) // <-- will print a
console.log('instance3 name: ' + instance3.name) // <-- will print test3
console.log('instance3 base: ' + instance3.base) // <-- will print 1234
```




<br><br>



# Event listener
- Instead of this we can use event.target (http://www.w3.org/TR/DOM-Level-2-Events/events.html)
```javascript
// example #1
export class User {
  personClick() {
    $(document).on('click', '.person', function(event) {
      const elem = event.target;
      $(elem).attr('data-active', 'true');
    });
  };
};


// example #2
class Cat extends EventEmitter {
  constructor() {
    super();
    this.on('wave', this.onWave);
  }
  onWave() {
    console.log('prototype wave');
  }
}

var cat = new Cat();
cat.emit('wave');
```






<br><br>



# Bind this to other method
- When you call a method with this you do not have access to this anymore. To solve this problem we use **.bind()**
```javascript
createDisconnectListener() {
    this.browser.on('disconnected', this._onDisconnect.bind(this) )
}

async _onDisconnect() {
    console.log('_onDisconnect')
    await this.connect()
}
```







<br><br>



# Private and public
- In this example private methods are still public accessable but you can tell other developer which methods are used outside by other files (public) and which methods are only used internal (private) in this class
```javascript
class BrowserWrapper {
    constructor(){
        this.example = true
    }

    // public
    async connect() {
        this.browser = true
	return this.browser
    }

    // private
    async _disconnect() {
        this.browser = false
	return this.browser
    }
}
	
const browser = new BrowserWrapper();
console.log(instance.example); //=> true
console.log(instance.connect()); //=> true
console.log(instance._disconnect()); //=> false
```

<br><br>
	
- In this example private methods are not public accessable
```javascript
class Something {
  #property;

  constructor(){
    this.#property = "test";
  }

  #privateMethod() {
    return 'hello world';
  }

  getPrivateMessage() {
      return this.#property;
  }
}

const instance = new Something();
console.log(instance.property); //=> undefined
console.log(instance.privateMethod); //=> undefined
console.log(instance.getPrivateMessage()); //=> test
console.log(instance.#property); //=> Syntax error
```
	
<br><br>

- In this example you can set private properties but not methods
```javascript
// Works too with new WeakMap();

// Works too without using Symbol just by declaring those variables out of scope from the class
const property = Symbol();
const hidden = Symbol();

class Something {
constructor(){
    this[property] = "test";
}

get() {
   return this[property]
}

/* not working */
//         [hidden]() {
//            return this[property]
//         }

//         public() {
//            return this.hidden()
//         }
}

var instance = new Something();

console.log(instance.property); // <-- undefined
console.log(instance.get()); // <-- test
```



	
	
	
	
	
	

<br><br><br><br>



# Service classes
- Service classes can be an extended subclass or you completly outsource them to a new file. The idea behind this is to outsource service function into a seperate space.
```javascript
// BrowserWrapper.js
const BrowserConnectionService = require('./BrowserConnectionService')

class BrowserWrapper {
  constructor(host, port){
      this.connectionService = new BrowserConnectionService(host, port)
  }
}


// BrowserConnectionService.js
module.exports = class BrowserConnectionService {
  constructor(host = process.env.CHROME_HOST, port = process.env.CHROME_PORT){
      this.chromeHost = host
      this.chromePort = port
  }
}
```


<br><br>



# Get class name
```javascript
class Rectangle {
    // Class constructor
    constructor(length, width) {
        this.length = length;
        this.width = width;
    }
    
    // Class method
    getArea() {
        return this.length * this.width;
    }
}
    
var rectObj = new Rectangle(5, 10);
console.log(rectObj.getArea()); // Outputs: 50
console.log(rectObj.constructor.name) // Outputs: Rectangle
```












<br><br>



# Object Destructuring with this
```javascript
class getThumbnailCfg {

  constructor(overrideCfg = {}){
    ({ banana: this.banana = false, apple: this.apple = {} } = overrideCfg)
    console.log(this.banana);
  }

}

var obj = {
  "banana": true,
  "apple": true
}
var test = new getThumbnailCfg(obj)
```

	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	

<br><br>



# Private Class Fields
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Private_class_fields

```javascript
class ClassWithPrivateField {
  #privateField;
}

class ClassWithPrivateMethod {
  #privateMethod() {
    return 'hello world';
  }
}

class ClassWithPrivateStaticField {
  static #PRIVATE_STATIC_FIELD;
}

class ClassWithPrivateStaticMethod {
  static #privateStaticMethod() {
    return 'hello world';
  }
}
	
	
	
	
	
	
	
	






// Example #1
class Something {
  #property;

  constructor(){
    this.#property = "test";
  }

  #privateMethod() {
    return 'hello world';
  }

  getPrivateMessage() {
      return this.#property;
  }
}

const instance = new Something();
console.log(instance.property); //=> undefined
console.log(instance.privateMethod); //=> undefined
console.log(instance.getPrivateMessage()); //=> test
console.log(instance.#property); //=> Syntax error
	

	
// Example #1
```




<br><br>
<br><br>


# Private Methods
```typescript
class Example {
    private privateMethod() {}
    public test() {}
}
```

<br><br>
<br><br>


## Test private Methods in TS
- https://github.com/CyberT33N/typescript-cheat-sheet/blob/main/README.md#test-private-methods

























<br><br>
<br><br>


# Get methods/properties of class instance
```typescript
const { ...object } = classInstance
```































<br><br>
<br><br>


# Assign class instance to class prototype
```typescript
# Method #1
Object.setPrototypeOf(currentClass, parentInstance)

# Method ä2
currentClass.prototype += parentInstance
```









<br><br>
<br><br>


# Field Declarations
```typescript
class Hello {
  counter = 0; // Class field
}
const myClass = new Hello();

let x = myClass.counter;
```







<br><br>
<br><br>


# Singleton with multiple instances

```typescript
/**
 * A utility class for managing MongoDB connections and schemas.
 */
class MongooseUtils {
    // A map to hold instances of MongooseUtils for different databases
    private static instances = new Map<string, MongooseUtils>()

    // MongoDB connection object
    private conn: mongoose.Connection | null = null

    // Connection string for MongoDB
    private connectionString: string

    /**
     * Private constructor to prevent direct instantiation.
     * @param {string} dbName - The name of the database to connect to.
     */
    private constructor(readonly dbName: string) {
        this.connectionString = process.env.MONGODB_CONNECTION_STRING!
    }

    /**
     * Gets an instance of MongooseUtils for a specified database.
     * If an instance does not exist, a new one will be created.
     * @param {string} dbName - The name of the database.
     * @returns An instance of MongooseUtils.
     */
    public static getInstance(dbName: string): MongooseUtils {
        if (!MongooseUtils.instances.has(dbName)) {
            MongooseUtils.instances.set(dbName, new MongooseUtils(dbName))
        }
        
        return MongooseUtils.instances.get(dbName)!
    }

    /**
     * Initializes the MongoDB connection.
     * @throws BaseError if the connection fails.
     */
    private async init(): Promise<void> {
        console.log('[ModelManager] - Attempting to connect to MongoDB...')

        this.updateConnectionString()

        try {
            this.conn = await mongoose.createConnection(this.connectionString).asPromise()
        } catch (e: unknown) {
            throw new BaseError(
                '[ModelManager] - Error while initializing connection with MongoDB', e as Error
            )
        }
    }

    /**
     * Updates the connection string to include the database name.
     */
    private updateConnectionString(): void {
        const urlObj = new URL(this.connectionString)
        urlObj.pathname = `/${this.dbName}`
        this.connectionString = urlObj.toString()
    }

    /**
     * Retrieves the current MongoDB connection.
     * If the connection is not established, it will initialize it first.
     * @returns A Promise that resolves to the MongoDB connection.
     */
    public async getConnection(): Promise<Connection> {
        if (!this.conn) {
            await this.init()
        }
        return this.conn!
    }
}

export default MongooseUtils

```
- This is how you can reset the instance in your test and test getInstance:
	```typescript
	    let mongooseUtils: MongooseUtils
	
	    const dbName = 'test'
	
	    beforeEach(() => {
	        (<any>MongooseUtils).instances = new Map()
	        mongooseUtils = MongooseUtils.getInstance(dbName)
	        expect(mongooseUtils).toBeInstanceOf(MongooseUtils)
	    })
	
	    describe('getInstance()', () => {
	        describe('[EXISTING INSTANCE]', () => {
	            beforeEach(() => {
	                ;(<any>mongooseUtils).changed = true
	            })
	             
	            it('should get existing instance for db', async() => {
	                const mongooseUtils2 = MongooseUtils.getInstance(dbName)
	                expect(mongooseUtils2).toEqual(mongooseUtils)
	
	                expect((<any>MongooseUtils).instances.size).toBe(1)
	                
	                expect(Reflect.get(mongooseUtils2, 'changed')).toBe(true)
	                expect(Reflect.get(mongooseUtils2, 'dbName')).toBe(dbName)
	            })
	        })
	        
	        describe('[NEW INSTANCE]', () => {
	            const dbName2 = 'test2'
	
	            it.only('should create new instance and set default properties', async() => {
	                expect(Reflect.get(mongooseUtils, 'dbName')).toBe(dbName)
	                expect(Reflect.get(mongooseUtils, 'conn')).toBe(null)
	                expect(Reflect.get(mongooseUtils, 'connectionString'))
	                .toBe(process.env.MONGODB_CONNECTION_STRING)
	            })
	
	            it.only('should create new instance if instance for db not exists', async() => {
	                // ==== INSTANCE #1 ====
	                expect((<any>MongooseUtils).instances.size).toBe(1)
	
	                // ==== INSTANCE #2 ====
	                const mongooseUtils2 = MongooseUtils.getInstance(dbName2)
	                expect(mongooseUtils2).toBeInstanceOf(MongooseUtils)
	                expect(mongooseUtils2).not.toEqual(mongooseUtils)
	
	                expect((<any>MongooseUtils).instances.size).toBe(2)
	            })
	        })
	    })
	```









<br><br>
<br><br>


# Unbound methods (methods without this)
- When you are using eslint and you are passing your class method to an event handler or you are writing a test then you will get the error [unbound-method](https://typescript-eslint.io/rules/unbound-method/). This will happen when your method is not a arrow function
```typescript
 /**
     * Updates the connection string to include the database name.
     * @returns {void} A void that esolves when the connection string is updated.
     */
    private updateConnectionString(): void {
        const urlObj = new URL(this.connectionString)
        urlObj.pathname = `/${this.dbName}`
        this.connectionString = urlObj.toString()
    }

```
```typescript
it('should verify return type', () => {
    expectTypeOf(mongooseUtils.updateConnectionString).returns.resolves
	.toEqualTypeOf<mongoose.Connection>()
})
```



For good writing style you should never define a public method when you are not using this context. Create a static instead. If wanted you can choose arrow funktion on your field declaration:
```typescript
    /**
     * Creates a Mongoose model based on the given name, schema, and database name.
     * @template TMongooseSchema - The type of the mongoose schema.
     * @param modelDetails - An object containing the model's details.
     * @returns A promise that resolves to the created Mongoose Model instance.
     */
    public createModel = async({
        modelName,
        schema,
        dbName
    })  => {
        const mongooseUtils = MongooseUtils.getInstance(dbName)
        const Model = await mongooseUtils.createModel(schema, modelName)
        
        // Ensure indexes are created for the model
        await Model.createIndexes()
        return Model
    }
```
- **NOTICE that sinon stub/spies will not work anymore with the the class prototype when you use arrow functions and maybe other things also not working. You can only use the instance. For this reason I would recommend to not use arrow functions in cases where you can the function to e.g. a event handler you should bind the instance to it .bind(classInstacne)**
```typescript
// Will not work anymore
initStub = sinon.stub(
    ModelManager.prototype, 'init' as keyof ModelManager
).resolves()

// Will work
initStub = sinon.stub(
    modelManager, 'init' as keyof ModelManager
).resolves()
```

<br><br>

But if you use this then you still should use an arrow function e.g or you keep the function as it is and use .bind(classInstacne). It depends how flexible you want to be:
```typescript
// Einfache Klasse mit einer Arrow Function und einer regulären Funktion
class MyClass {
  constructor() {
    this.name = 'Dennis';
  }

  // Reguläre Funktion
  regularFunction() {
    console.log('Regular Function:', this.name);
  }

  // Arrow Function
  arrowFunction = () => {
    console.log('Arrow Function:', this.name);
  }
}

const myObject = new MyClass();

// Test der Methoden ohne Kontextverlust
myObject.regularFunction(); // Ausgabe: "Regular Function: Dennis"
myObject.arrowFunction(); // Ausgabe: "Arrow Function: Dennis"

// Kontextverlust: Wir übergeben die Methoden als Callback
const regularCallback = myObject.regularFunction;
const arrowCallback = myObject.arrowFunction;

regularCallback(); // Ausgabe: "Regular Function: undefined" (Kontextverlust) <-- Will throw error
arrowCallback();   // Ausgabe: "Arrow Function: Dennis" (Beibehaltung des Kontexts)

```


### Should I always use arrow functions?

Not always, but **often**. Arrow functions are useful when you want to ensure that the `this` context is **preserved**, especially in callbacks or event handlers. They give you the advantage of not needing to explicitly `bind(this)`, which makes the code cleaner.

### When **arrow functions** make sense:
1. **Callbacks and Event Handlers**: Arrow functions are ideal when passing a method as a callback without losing the context.
   ```javascript
   button.addEventListener('click', this.handleClick); // Might lose context
   button.addEventListener('click', () => this.handleClick()); // Arrow function keeps `this`
   ```

2. **Avoiding `bind(this)`**: You don't need to worry about using `bind(this)` to explicitly set the context.

### When **regular functions** are better:
1. **If you use inheritance** and implement polymorphic functions, it's better to use regular methods.
2. **If you want to adjust functions dynamically** (e.g., using `call` or `apply`), you need the flexibility of regular functions since arrow functions cannot be rebound.

### Rule of Thumb:
- **Arrow Functions**: Use them when you don't want to deal with the `this` context, which is most of the time. They are particularly helpful in modern JavaScript and TypeScript projects.
- **Regular Methods**: Use them when you need to explicitly change the context, or in cases involving inheritance and complex object structures.

Try it in your code, but in many situations, arrow functions will help you avoid many `this` context issues.
