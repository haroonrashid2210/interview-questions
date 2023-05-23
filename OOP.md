# Inheritance

In JavaScript, inheritance is a mechanism that allows objects to inherit properties and methods from a parent object or class. It enables code reuse and the creation of hierarchical relationships between objects.

Here's a concise example of inheritance in JavaScript:

```javascript
// Parent class
class Animal {
  constructor(name) {
    this.name = name;
  }

  eat() {
    console.log(this.name + ' is eating.');
  }
}

// Child class inheriting from Animal
class Dog extends Animal {
  bark() {
    console.log(this.name + ' is barking.');
  }
}

// Create instances
const animal = new Animal('Generic Animal');
const dog = new Dog('Bobby');

// Use inherited methods
animal.eat(); // Output: Generic Animal is eating.
dog.eat();    // Output: Bobby is eating.

// Use methods specific to the child class
dog.bark();   // Output: Bobby is barking.
```

In the example above, the `Animal` class is the parent class, and the `Dog` class is the child class that inherits from `Animal`. The `Dog` class extends the functionality of the `Animal` class by adding a `bark()` method.

Instances of both `Animal` and `Dog` can call the inherited `eat()` method, but only the `Dog` instance can call the `bark()` method because it is specific to the `Dog` class.









# Encapsulation

Encapsulation in Object-Oriented Programming (OOP) is a principle that involves bundling data and the methods that operate on that data into a single unit called a class. It allows for the hiding of internal state and implementation details, and provides access to the data through defined interfaces.

Here's a short and concise example of encapsulation in JavaScript:

```javascript
class Car {
  constructor(make, model) {
    this.make = make; // public property
    this.model = model; // public property
    this._mileage = 0; // private property, denoted by underscore
  }

  get mileage() {
    return this._mileage; // getter for private property
  }

  set mileage(value) {
    if (value >= 0) {
      this._mileage = value; // setter for private property
    }
  }

  drive(distance) {
    this._mileage += distance;
  }
}

const myCar = new Car('Toyota', 'Camry');
myCar.drive(100);
console.log(myCar.mileage); // Output: 100
```

In this example, the `Car` class encapsulates the data related to a car (make, model, and mileage) and provides methods (`drive`) to modify and retrieve the data. The `mileage` property is encapsulated as a private property using the underscore convention (`_mileage`), and it can only be accessed through the getter and setter methods (`get mileage()` and `set mileage()`). This encapsulation ensures that the internal state of the car is controlled and accessed only through the defined interface, providing better control and abstraction.









# Polymorphism

Polymorphism in object-oriented programming (OOP) refers to the ability of objects of different types to be treated as objects of a common parent class. It allows methods in the parent class to be overridden by the child classes, providing different implementations for the same method name.

Here's an example of polymorphism in JavaScript:

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  sound() {
    console.log("The animal makes a sound.");
  }
}

class Dog extends Animal {
  sound() {
    console.log("The dog barks.");
  }
}

class Cat extends Animal {
  sound() {
    console.log("The cat meows.");
  }
}

// Polymorphic behavior
const animals = [
  new Dog("Buddy"),
  new Cat("Whiskers")
];

animals.forEach(animal => {
  animal.sound(); // Calls the overridden sound method based on the actual object type
});
```

In this example, we have an `Animal` base class and two derived classes, `Dog` and `Cat`. Each derived class overrides the `sound` method from the `Animal` class with its own implementation.

The `animals` array contains objects of different types, including both dogs and cats. When we iterate over the array and call the `sound` method on each object, the appropriate implementation is called based on the actual object type. This is the essence of polymorphism, where different objects are treated uniformly through a common interface, but exhibit different behaviors based on their specific type.









# Data abstraction

Data abstraction in object-oriented programming (OOP) refers to the process of hiding the implementation details of a class and exposing only the essential features or behaviors to the outside world. It allows you to focus on what an object does rather than how it does it.

In JavaScript, you can achieve data abstraction using techniques such as encapsulation and information hiding. Here's a simple example to illustrate data abstraction in JavaScript:

```javascript
// Creating a Car class with data abstraction
class Car {
  constructor(make, model) {
    this.make = make; // Public property
    this.model = model; // Public property
    this._mileage = 0; // Private property
  }

  // Public method to get the mileage
  getMileage() {
    return this._mileage;
  }

  // Public method to update the mileage
  updateMileage(miles) {
    if (miles > 0) {
      this._mileage += miles;
    }
  }
}

// Creating an instance of the Car class
const myCar = new Car("Toyota", "Camry");

// Accessing public properties
console.log(myCar.make); // Output: Toyota
console.log(myCar.model); // Output: Camry

// Updating the mileage through public method
myCar.updateMileage(500);
console.log(myCar.getMileage()); // Output: 500

// Trying to access the private property directly
console.log(myCar._mileage); // Output: undefined (Private property)
```

In this example, the `Car` class encapsulates the properties `make`, `model`, and `_mileage`. The `make` and `model` properties are public and can be accessed directly. However, the `_mileage` property is marked as private by prefixing it with an underscore. It can only be accessed or modified through the public methods `getMileage()` and `updateMileage()` respectively. This hides the internal implementation details from the external code, achieving data abstraction.









# Composition

Composition in object-oriented programming (OOP) refers to the concept of building complex objects by combining smaller, more manageable objects. It allows objects to be composed of other objects as components, enabling code reuse and creating flexible and modular systems.

In JavaScript, composition can be achieved by creating objects that contain references to other objects, effectively delegating specific functionalities to those objects. Here's a concise example to illustrate composition in JavaScript:

```javascript
// Example 1: Composition using object references

// Create a 'engine' object with a 'start' method
const engine = {
  start() {
    console.log("Engine started");
  },
};

// Create a 'car' object composed of the 'engine' object
const car = {
  engine: engine,
  drive() {
    this.engine.start();
    console.log("Car driving");
  },
};

// Use the 'car' object
car.drive();
// Output:
// Engine started
// Car driving


// Example 2: Composition using object destructuring

// Create a 'battery' object with a 'charge' method
const battery = {
  charge() {
    console.log("Battery charged");
  },
};

// Create a 'smartphone' object composed of the 'battery' object
const smartphone = {
  ...battery,
  call() {
    console.log("Smartphone calling");
  },
};

// Use the 'smartphone' object
smartphone.charge();
smartphone.call();
// Output:
// Battery charged
// Smartphone calling
```

In the examples above, composition is achieved by creating objects (`car` and `smartphone`) that include references to other objects (`engine` and `battery`, respectively). This allows the composed objects to utilize the functionalities provided by the referenced objects, resulting in modular and reusable code structures.









# Overloading and overriding

Overloading and overriding are two important concepts in object-oriented programming (OOP). Here's a brief explanation of each with an example in JavaScript:

1. Overloading:
Overloading refers to the ability to define multiple methods with the same name but different parameters. The appropriate method to be called is determined by the number and types of arguments passed to it. However, JavaScript does not support method overloading natively. Nevertheless, you can simulate method overloading by checking the number of arguments or their types within a single method.

Example:
```javascript
class Calculator {
  add(a, b) {
    return a + b;
  }

  add(a, b, c) {
    return a + b + c;
  }
}

const calc = new Calculator();
console.log(calc.add(2, 3));       // Output: NaN
console.log(calc.add(2, 3, 4));    // Output: 9
```
In JavaScript, the last defined method with the same name will override the previous one. So in the example above, when you call `calc.add(2, 3)`, it will invoke the second `add` method with three parameters. However, since the first `add` method is not accessible, it results in `NaN`.

2. Overriding:
Overriding occurs when a derived class provides its own implementation of a method that is already defined in its parent class. The purpose is to modify or extend the behavior of the inherited method. In JavaScript, you can achieve method overriding through inheritance using the `class` keyword.

Example:
```javascript
class Animal {
  speak() {
    return "Animal speaks";
  }
}

class Dog extends Animal {
  speak() {
    return "Dog barks";
  }
}

const animal = new Animal();
console.log(animal.speak());    // Output: "Animal speaks"

const dog = new Dog();
console.log(dog.speak());       // Output: "Dog barks"
```
In this example, the `Animal` class has a `speak` method, and the `Dog` class extends `Animal`. The `Dog` class overrides the `speak` method with its own implementation. When you call `dog.speak()`, it invokes the overridden `speak` method defined in the `Dog` class, returning `"Dog barks"` instead of the default `"Animal speaks"` from the `Animal` class.









# Cohession

