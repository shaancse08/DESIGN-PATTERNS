## Singleton Pattern

The singleton pattern is a way to structure your code so that you can’t have more than one instance of your logic, ever.

In case it wasn’t obvious yet, these patterns are meant for the Object-Oriented Programming paradigm. This means that the above sentence can be translated to:

###### By implementing a singleton we can ensure we only have one instance of our class, ever.

The below code we use to implement the Singleton Pattrn

```javascript
class MySingleton {
    // Object which is a static
    static instance: MySingleton;
    // Constructor is private here
    private constructor() {
        console.log("constructor called!");
    }
    // Creating instance is only possible using this method
    public static getInstance(): MySingleton {
        if (!MySingleton.instance) {
            MySingleton.instance = new MySingleton();
        }
        return MySingleton.instance;
    }

    public logic() {
        console.log("my logic!");
    }
}

// Creating the instance
let myInstance: MySingleton = MySingleton.getInstance();
myInstance.logic();
```


#### Real life example of a Singleton pattern
Logging is an nice example of singleton pattern. We've all done it, adding logs throughout your code is usually a must, especially for big projects. Enabling, disabling them and even changing their default level can be a pain if you don't centralize the code in a single entity — i.e "the logger". By having your logger be a singleton, you ensure only one in-memory instance of it is recording your data (instead of accidentally instantiating several at once, and having them sending repeated messages).