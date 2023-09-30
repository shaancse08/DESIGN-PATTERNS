## Factory Design Pattern

When crafting software applications, one of the most pivotal considerations is the creation of objects. Notably, we often need to create objects that share a common interface, but their exact type may only be determinable at runtime. Wouldn’t it be perfect if we could encapsulate this object creation process in its own entity? That’s where the Factory Design Pattern comes in!

**A Blueprint for Object Creation — The Factory Pattern**
Think of the Factory Pattern as a central authority or a blueprint that handles the object instantiation process. Drawing parallels to real-world manufacturing, an architect designing buildings doesn’t have to worry about the intricacies of how bricks are made or how glass is manufactured. They rely on the factories producing these components, according to their specifications, ready to fit in their architectural designs.

In software design, the Factory Pattern serves a similar purpose. It takes care of object creation and delivers the newly constructed instances ready for use, abstracting the object creation complexities from the consumer.

#### Why Is It So Important?

The Factory Design Pattern is pivotal for three primary reasons:

- **Loose coupling:** The factory encapsulates the creation details and returns an instance of a common interface, ensuring that the main application isn’t tightly bound to the specific object types.
- **Code reusability and modularity:** Centralizing object creation in a single place naturally promotes reusability. It also makes the system more modular since any changes in object creation only affect the factory, not the consumer.
- **Flexibility and scalability:** When a new object type needs to be added, only the factory needs an update. The consumer code remains untouched, making the system scalable and easy to maintain.

#### When Should We Use It?

Factory Pattern shines in scenarios where:

- A class cannot anticipate the type of objects it needs to create.
- A class delegates responsibilities to helper subclasses, and the knowledge of which helper class is the best suited for the job needs to be localized.
- Objects created share a common interface, but their specific type might be determined at runtime.

In essence, the Factory Design Pattern is an ideal choice when dealing with a set of related object types, and there’s a need to manage these types in a clean, scalable, and loosely coupled manner.

#### Steps to create Factory Design Pattern

- **Step 1: Define the Product Interface**: First off, we define a common interface for our products. This interface serves as the blueprint for creating objects in our factory. For our example, we’ll use a Car interface:

```javascript
interface Car {
  model: string;
  drive(): void;
}
```

- **Step 2: Implement Concrete Products**: The next step is to create some concrete Car classes that implement the Car interface. Here we define Tesla and Mercedes as the types of cars our factory will be able to create:

```javascript
class Tesla implements Car {
  model = "Tesla";

  drive() {
    console.log(`You are driving a ${this.model}`);
  }
}

class Mercedes implements Car {
  model = "Mercedes";

  drive() {
    console.log(`You are driving a ${this.model}`);
  }
}
```

- **Step 3: Create the Factory**: Now, let’s create the CarFactory class. This factory’s job is to create and return instances of Car. The specifics of what type of car gets created is determined at runtime:

```javascript
class CarFactory {
  createCar(type: string): Car {
    if (type === "Tesla") {
      return new Tesla();
    } else if (type === "Mercedes") {
      return new Mercedes();
    } else {
      throw new Error("Car type not supported");
    }
  }
}
```

- **Step 4: Factory Usage**: Finally, let’s see how to use the factory in practice. We create a CarFactory instance and use it to create a Tesla and a Mercedes:

```javascript
const carFactory = new CarFactory();

const myTesla = carFactory.createCar("Tesla");
myTesla.drive(); // Outputs: You are driving a Tesla

const myMercedes = carFactory.createCar("Mercedes");
myMercedes.drive(); // Outputs: You are driving a Mercedes
```

###### Below is the complete code to implement Factory Design Pattern.

```javascript
// Step 1: Define the Product Interface
interface Car {
  model: string;
  drive(): void;
}

// Step 2: Implement Concrete Products
class Tesla implements Car {
  model = "Tesla";

  drive() {
    console.log(`You are driving a ${this.model}`);
  }
}

class Mercedes implements Car {
  model = "Mercedes";

  drive() {
    console.log(`You are driving a ${this.model}`);
  }
}

// Step 3: Create the Factory
class CarFactory {
  createCar(type: string): Car {
    if (type === "Tesla") {
      return new Tesla();
    } else if (type === "Mercedes") {
      return new Mercedes();
    } else {
      throw new Error("Car type not supported");
    }
  }
}

// Step 4: Factory Usage
const carFactory = new CarFactory();

const myTesla = carFactory.createCar("Tesla");
myTesla.drive(); // Outputs: You are driving a Tesla

const myMercedes = carFactory.createCar("Mercedes");
myMercedes.drive(); // Outputs: You are driving a Mercedes
```
