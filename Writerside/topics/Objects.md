# Objects

## Real Life Objects

In real life, `objects` are things like: houses, cars, people, animals, or any other subjects.

Here is a car object example:
![image_3.png](image_3.png)

### Object Properties
A real life car has properties like weight and color:

`car.name = Fiat`, `car.model = 500`, `car.weight = 850kg`, `car.color = white`.

Car objects have the same `properties`, but the `values` differ from car to car.

### Object Methods
A real life car has methods like start and stop:

`car.start()`, `car.drive()`, `car.brake()`, `car.stop()`.

Car objects have the same methods, but the methods are performed at different times.

## Creating a JavaScript Object
```js
// Create an Object
const person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```
Spaces and line breaks are not important. An object initializer can span multiple lines:
```js
// Create an Object
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};
```
This example creates an empty JavaScript object, and then adds 4 properties:
```js
// Create an Object
const person = {};

// Add Properties
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```
### Using the new Keyword
```js
// Create an Object
const person = new Object();

// Add Properties
person.firstName = "John";
person.lastName = "Doe";
person.age = 50;
person.eyeColor = "blue";
```

## Object Properties {id="object-properties_1"}
The named values, in JavaScript objects, are called properties.

| Property   | Value  |
|------------|--------|
| firstName  | John   |
| lastName   | Doe    |
| age        | 50     |
| eyeColor   | blue   |

Objects written as name value pairs are similar to:
* Associative arrays in PHP
* Dictionaries in Python
* Hash tables in C
* Hash maps in Java
* Hashes in Ruby and Perl

## Accessing Object Properties
You can access object properties in two ways:
```js
objectName.propertyName
```

```js
objectName["propertyName"]
```

## JavaScript Object Methods
Methods are actions that can be performed on objects.

Methods are function definitions stored as property values.
```js
const person = {
  firstName: "John",
  lastName : "Doe",
  id       : 5566,
  fullName : function() {
    return this.firstName + " " + this.lastName;
  }
};
```
## In JavaScript, Objects are King.
If you Understand Objects, you Understand JavaScript.
In JavaScript, almost "everything" is an object.

* Objects are objects
* Maths are objects
* Functions are objects
* Dates are objects
* Arrays are objects
* Maps are objects
* Sets are objects

## JavaScript Primitives
A `primitive value` is a value that has no properties or methods.

`3.14` is a primitive value

A `primitive data type` is data that has a primitive value.

JavaScript defines 7 types of primitive data types:

* string
* number
* boolean
* null
* undefined
* symbol
* bigint

> Immutable : 
Primitive values are immutable (they are hardcoded and cannot be changed). if x = 3.14, you can change the value of x, but you cannot change the value of 3.14.

## JavaScript Objects are Mutable
Objects are mutable: They are addressed by reference, not by value.

If person is an object, the following statement will not create a copy of person:

* The object x is not a copy of person. The object x is person.
* The object x and the object person share the same memory address.
* Any changes to x will also change person:

```js
//Create an Object
const person = {
  firstName:"John",
  lastName:"Doe",
  age:50, eyeColor:"blue"
}

// Try to create a copy
const x = person;

// This will change age in person:
x.age = 10;
```
