# Object Oriented Programing

### Object-Oriented Programming (OOP) in JavaScript

Object-Oriented Programming (OOP) is a programming paradigm that uses objects and classes to organize code. In JavaScript, objects are the fundamental building blocks of OOP, and they are used to store related data and functions. OOP in JavaScript is based on prototypes, but with the introduction of **ES6 classes**, JavaScript now offers a more familiar class-based approach for creating and organizing objects.

Let's break down OOP concepts in JavaScript and provide examples to help you understand how it works.

---

### 1. **Objects and Properties**

In JavaScript, an **object** is a collection of key-value pairs, where keys are strings (or symbols) and values can be any data type (including functions).

#### Example:

```javascript
// Creating an object in JavaScript
let person = {
    name: "John",
    age: 30,
    greet: function() {
        console.log("Hello, " + this.name);
    }
};

// Accessing object properties
console.log(person.name); // John
console.log(person.age);  // 30
person.greet();           // Hello, John
```

#### Explanation:

* `person` is an object with properties `name`, `age`, and a method `greet()`.
* We use `person.name` to access the `name` property, and `person.greet()` to call the method.

---

### 2. **Classes and Constructors**

Before ES6, JavaScript used **constructor functions** to create and initialize objects. ES6 introduced the **class** syntax, which is more readable and familiar to developers with experience in languages like Java or C++.

#### Example: Creating Classes

```javascript
// ES6 Class definition
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }

    greet() {
        console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    }
}

// Creating an instance of the class
let john = new Person("John", 30);
john.greet();  // "Hello, my name is John and I am 30 years old."
```

#### Explanation:

* The `constructor` method is called when a new instance of the class is created. It initializes the properties of the object.
* `greet()` is a method that can be called on instances of the `Person` class.

---

### 3. **Inheritance in JavaScript**

In OOP, **inheritance** allows one class (the child class) to inherit properties and methods from another class (the parent class). JavaScript uses prototypes for inheritance.

#### Example: Inheritance with ES6 Classes

```javascript
// Parent class
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a sound`);
    }
}

// Child class (inherits from Animal)
class Dog extends Animal {
    constructor(name, breed) {
        super(name); // Call the parent class constructor
        this.breed = breed;
    }

    speak() {
        console.log(`${this.name} barks`);
    }
}

// Creating instances
let dog = new Dog("Max", "Golden Retriever");
dog.speak();  // "Max barks"
```

#### Explanation:

* `Dog` is a subclass of `Animal`. It inherits the `speak()` method from the parent class but overrides it with its own implementation.
* `super(name)` is used to call the constructor of the parent class `Animal`.

---

### 4. **Encapsulation**

**Encapsulation** is the concept of bundling data (properties) and methods (functions) that operate on the data into a single unit (class). It also refers to restricting access to some of an object's components, making the object more secure and its implementation hidden.

#### Example: Private Properties (using closures)

```javascript
class Person {
    constructor(name, age) {
        let _name = name; // private variable
        let _age = age;   // private variable

        this.getName = function() {
            return _name;
        };

        this.getAge = function() {
            return _age;
        };

        this.setAge = function(newAge) {
            if (newAge > 0) {
                _age = newAge; // We can modify _age through a method
            }
        };
    }
}

let person = new Person("John", 30);
console.log(person.getName()); // John
console.log(person.getAge());  // 30

person.setAge(35);
console.log(person.getAge());  // 35

// person._age = 40; // Cannot directly access _age
console.log(person.getAge());  // 35
```

#### Explanation:

* `_name` and `_age` are **private** variables because they are not directly accessible from outside the class.
* `getName()`, `getAge()`, and `setAge()` are **public** methods that provide controlled access to the private properties.
* This is an example of **encapsulation**, where data is hidden, and access is provided through getter and setter methods.

---

### 5. **Polymorphism**

**Polymorphism** refers to the ability of different classes to respond to the same method in different ways. In JavaScript, this is often achieved through method overriding.

#### Example: Polymorphism with Method Overriding

```javascript
// Parent class
class Animal {
    speak() {
        console.log("The animal makes a sound");
    }
}

// Child class 1
class Dog extends Animal {
    speak() {
        console.log("The dog barks");
    }
}

// Child class 2
class Cat extends Animal {
    speak() {
        console.log("The cat meows");
    }
}

// Instances
let dog = new Dog();
let cat = new Cat();

dog.speak();  // "The dog barks"
cat.speak();  // "The cat meows"
```

#### Explanation:

* Both `Dog` and `Cat` override the `speak()` method from `Animal`.
* Despite having the same method name, each class implements its version of the `speak()` method. This is **polymorphism** in action.

---

### 6. **Method Chaining**

Method chaining is a technique where multiple methods are called on the same object in a single statement. It can be achieved by having each method return the object (`this`).

#### Example: Method Chaining

```javascript
class Car {
    constructor(make, model) {
        this.make = make;
        this.model = model;
        this.speed = 0;
    }

    accelerate(amount) {
        this.speed += amount;
        return this;  // Return the object itself for chaining
    }

    brake(amount) {
        this.speed -= amount;
        return this;  // Return the object itself for chaining
    }

    displaySpeed() {
        console.log(`Current speed: ${this.speed} km/h`);
        return this;  // Return the object itself for chaining
    }
}

let car = new Car("Toyota", "Corolla");
car.accelerate(50).brake(20).displaySpeed();  // "Current speed: 30 km/h"
```

#### Explanation:

* Methods `accelerate()`, `brake()`, and `displaySpeed()` return `this`, which allows them to be chained together in a single statement.

---

### 7. **Static Methods**

**Static methods** are methods that belong to the class itself, rather than to instances of the class. They are often used for utility functions or helper methods that don't depend on instance data.

#### Example: Static Methods

```javascript
class MathHelper {
    static add(a, b) {
        return a + b;
    }

    static multiply(a, b) {
        return a * b;
    }
}

console.log(MathHelper.add(5, 3));      // 8
console.log(MathHelper.multiply(5, 3)); // 15
```

#### Explanation:

* `add()` and `multiply()` are **static methods** that are called on the class itself (`MathHelper.add()`), not on instances of the class.

---