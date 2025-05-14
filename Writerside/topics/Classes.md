# Object Oriented Programing in TS

Object-Oriented Programming (OOP) is a paradigm that uses objects and classes to organize code. TypeScript is a superset of JavaScript that introduces strong typing and better tools for working with OOP concepts.

Let's break down the OOP concepts and how they work in TypeScript.

---

### 1. **Objects and Properties**

In TypeScript, an **object** is a collection of key-value pairs. You can define an object using interfaces or classes, and types can be specified for both keys and values.

#### Example:

```ts
class Person {
    // Properties
    name: string;
    age: number;
    gender: string;
    // constructor
    constructor(_name: string, _age: number, _gender: string) {
        this.name = _name;
        this.age = _age;
        this.gender = _gender;
    }
    // methods
    greet():void {
        console.log(`hello , my name is ${this.name} and I'm ${this.age} years old.`)
    }
}
// Accessing object properties
console.log(person.name); // John
console.log(person.age);  // 30
person.greet();           // Hello, John
```

##### Explanation:

* We define an interface `Person` with properties and methods.
* Type annotations ensure `name` is a string, `age` is a number, and `greet` is a method.

---

### 2. **Classes and Constructors**

In TypeScript, we can define classes and use the `constructor` method to initialize properties of an object.

#### Example: Creating Classes

```ts
class Person {
    name: string;
    age: number;

    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }

    greet(): void {
        console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    }
}

// Creating an instance of the class
const john = new Person("John", 30);
john.greet();  // "Hello, my name is John and I am 30 years old."
```

##### Explanation:

* The `constructor` initializes the `name` and `age` properties.
* The `greet()` method can be called on instances of the class.

---

### 3. **Inheritance in TypeScript**

Inheritance allows a class (child class) to inherit properties and methods from another class (parent class). TypeScript uses the `extends` keyword for inheritance.

#### Example: Inheritance with TypeScript Classes

```ts
// Parent class
class Animal {
    name: string;

    constructor(name: string) {
        this.name = name;
    }

    speak(): void {
        console.log(`${this.name} makes a sound`);
    }
}

// Child class (inherits from Animal)
class Dog extends Animal {
    breed: string;

    constructor(name: string, breed: string) {
        super(name);  // Call the parent class constructor
        this.breed = breed;
    }

    speak(): void {
        console.log(`${this.name} barks`);
    }
}

// Creating instances
const dog = new Dog("Max", "Golden Retriever");
dog.speak();  // "Max barks"
```

##### Explanation:

* `Dog` extends `Animal`, inheriting its properties and methods.
* `super(name)` calls the constructor of the parent class.
* The `speak()` method is overridden in `Dog` to provide specific functionality.

#### Bank Account Scenario
```typescript

// parent class
class BankAccount {
    constructor(public balance: number, public accountHolder: string) {
    }

    public deposit(amount: number): void {
        if (this.validateBalance(amount)) {
            this.balance += amount   // balance = balance + amount  
        }
    }

    public getBalance(): number {
        return this.balance
    }

    public withDraw(amount: number): number | string {
        if (this.canWithDraw(amount)) {
            return this.balance -= amount   // balance = balance - amount         
        } else {
            return `your account balance : ${this.balance} is less than the amount you want to withdraw : ${amount}`
        }
    }

    private validateBalance(amount: number): boolean {
        return amount > 0;
    }

    private canWithDraw(amountToWithDraw: number): boolean {
        return this.balance > amountToWithDraw
    }

}

// child class
class SavingAccount extends BankAccount {
    public interestRate: number;
    constructor(accountHolder: string, balance: number, _interestRate: number) {
        super(balance, accountHolder)
        this.interestRate = _interestRate
    }

    public getBalance(): number {
        return this.balance
    }

    public calculateInterest(): void {
        const interest = this.getBalance() * this.interestRate;
        console.log(`interest earned : ${interest}`)
        this.balance += interest
    }
}


// const kevinAccount = new BankAccount(300, "Keren");
// console.log(kevinAccount.getBalance())
// kevinAccount.deposit(1000)
// console.log(kevinAccount.getBalance())
// console.log(kevinAccount.withDraw(1000))
// console.log(kevinAccount.getBalance())

const kerenAccount = new SavingAccount("keren", 300, 0.05)

kerenAccount.deposit(1000)

kerenAccount.calculateInterest()

console.log(kerenAccount.getBalance())
```
---

### 4. **Access Modifiers: Public, Private, and Protected**

Access modifiers are used to control the visibility of class members. In TypeScript, you have three types of access modifiers:

* **Public**: Members are accessible from anywhere.
* **Private**: Members are only accessible within the class.
* **Protected**: Members are accessible within the class and derived classes (subclasses).

#### Example:

```ts
class Person {
    public name: string;
    private age: number;
    protected address: string;

    constructor(name: string, age: number, address: string) {
        this.name = name;
        this.age = age;
        this.address = address;
    }

    greet(): void {
        console.log(`Hello, my name is ${this.name}`);
    }

    getAge(): number {
        return this.age;  // Access private variable through a method
    }
}

const person = new Person("John", 30, "123 Main St");
console.log(person.name); // public, can be accessed outside
console.log(person.getAge()); // private, accessed via method

// console.log(person.age); // Error: age is private
```

##### Explanation:

* `name` is `public`, so it can be accessed directly.
* `age` is `private`, so it can only be accessed within the class.
* `address` is `protected`, so it can be accessed within the class and subclasses.

---

### 5. **Getters and Setters**

Getters and setters allow you to control access to private properties of a class. They allow you to execute code when accessing or modifying a property.

#### Example:

```ts
class Person {
    private _age: number;

    constructor(age: number) {
        this._age = age;
    }

    get age(): number {
        return this._age;
    }

    set age(value: number) {
        if (value > 0) {
            this._age = value;
        } else {
            console.log("Age must be positive");
        }
    }
}

const person = new Person(30);
console.log(person.age); // 30 (via getter)
person.age = 35; // 35 (via setter)
console.log(person.age); // 35
person.age = -5; // Error: Age must be positive
```

##### Explanation:

* The `age` property is accessed using the getter and setter.
* The setter checks for valid input before modifying the private `_age` property.

---

### 6. **Encapsulation**

Encapsulation refers to bundling the data (properties) and methods (functions) that operate on the data into a single unit (class). It also refers to restricting access to some of an object's components to make the object more secure.

In TypeScript, we can achieve encapsulation with **private** and **protected** members.

#### Example:

```ts
class Person {
    private _name: string;
    private _age: number;

    constructor(name: string, age: number) {
        this._name = name;
        this._age = age;
    }

    getName(): string {
        return this._name;
    }

    getAge(): number {
        return this._age;
    }

    setAge(age: number): void {
        if (age > 0) {
            this._age = age;
        }
    }
}

const person = new Person("John", 30);
console.log(person.getName()); // John
console.log(person.getAge());  // 30
person.setAge(35);
console.log(person.getAge());  // 35
```

##### Explanation:

* The `_name` and `_age` properties are private and not directly accessible from outside the class.
* The `getName()`, `getAge()`, and `setAge()` methods are used to control access to these private properties.

---

### 7. **Polymorphism**

Polymorphism is the ability of different classes to respond to the same method in different ways. In TypeScript, polymorphism is often achieved through method overriding.

#### Example:

```ts
class Animal {
    speak(): void {
        console.log("The animal makes a sound");
    }
}

class Dog extends Animal {
    speak(): void {
        console.log("The dog barks");
    }
}

class Cat extends Animal {
    speak(): void {
        console.log("The cat meows");
    }
}

const dog = new Dog();
const cat = new Cat();

dog.speak(); // "The dog barks"
cat.speak(); // "The cat meows"
```

##### Explanation:

* `Dog` and `Cat` override the `speak()` method from `Animal`.
* Despite having the same method name, each class implements its own version of `speak()`.

---

### 8. **Static Methods**

Static methods are methods that belong to the class itself, not instances of the class. These methods are useful for utility functions that do not depend on instance data.

#### Example:

```ts
class MathHelper {
    static add(a: number, b: number): number {
        return a + b;
    }

    static multiply(a: number, b: number): number {
        return a * b;
    }
}

console.log(MathHelper.add(5, 3));      // 8
console.log(MathHelper.multiply(5, 3)); // 15
```

###### Explanation:

* `add()` and `multiply()` are **static methods** that can be called directly on the class (`MathHelper.add()`), not on instances of the class.

---