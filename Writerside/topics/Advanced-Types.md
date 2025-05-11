# Advanced Types

### **Advanced Types in TypeScript**

TypeScript provides several advanced types and features to help manage complex data structures while maintaining type safety. Here’s an explanation of advanced types in TypeScript with examples:

---

### 1. **Literal Types**

Literal types allow you to specify the exact value a string, number, or boolean variable can hold, making the type more specific than the general `string`, `number`, or `boolean`.

#### Example:

```typescript
let myName: "John" = "John";  // The value must always be "John"
myName = "Alice";  // Error: Type '"Alice"' is not assignable to type '"John"'

let isActive: true = true;  // The value must always be `true`
isActive = false;  // Error: Type 'false' is not assignable to type 'true'
```

In this example, `myName` is strictly limited to the string `"John"`, and `isActive` can only be `true`.

---

### 2. **Union Types**

Union types allow a variable to hold values of more than one type. You can define a union type using the pipe (`|`) symbol.

#### Example:

```typescript
let result: string | number;

result = "Hello, world!";  // Valid
result = 42;  // Valid
result = true;  // Error: Type 'boolean' is not assignable to type 'string | number'
```

In this example, the variable `result` can either be a `string` or a `number`.

---

### 3. **Intersection Types**

Intersection types allow you to combine multiple types into one. A variable of an intersection type must satisfy all of the combined types.

#### Example:

```typescript
type Person = {
  name: string;
  age: number;
};

type Address = {
  street: string;
  city: string;
};

type PersonWithAddress = Person & Address;

const personWithAddress: PersonWithAddress = {
  name: "Alice",
  age: 30,
  street: "123 Main St",
  city: "Wonderland",
};
```

In this example, the `PersonWithAddress` type combines the `Person` and `Address` types, meaning the object must have both personal information and address details.

---

### 4. **Instanceof Type Guard**

The `instanceof` operator in TypeScript can be used as a type guard to narrow the type of an object based on its class.

#### Example:

```typescript
class Dog {
  bark() {
    console.log("Woof!");
  }
}

class Cat {
  meow() {
    console.log("Meow!");
  }
}

function animalSound(animal: Dog | Cat) {
  if (animal instanceof Dog) {
    animal.bark();
  } else {
    animal.meow();
  }
}

const dog = new Dog();
const cat = new Cat();

animalSound(dog);  // Output: Woof!
animalSound(cat);  // Output: Meow!
```

Here, `instanceof` is used to determine whether the object is an instance of the `Dog` or `Cat` class, and we can call the respective method based on the type.

---

### 5. **Discriminated Unions (Tagged Unions)**

Discriminated unions allow you to use a common property (tag) to distinguish between different types within a union. This is useful when you have different object shapes but share a common property that acts as a discriminator.

#### Example:

```typescript
type Circle = {
  shape: "circle";
  radius: number;
};

type Square = {
  shape: "square";
  sideLength: number;
};

type Shape = Circle | Square;

function area(shape: Shape): number {
  if (shape.shape === "circle") {
    return Math.PI * shape.radius ** 2;
  } else {
    return shape.sideLength ** 2;
  }
}

const circle: Circle = { shape: "circle", radius: 10 };
const square: Square = { shape: "square", sideLength: 5 };

console.log(area(circle));  // Output: 314.1592653589793
console.log(area(square));  // Output: 25
```

In this example, the `shape` property serves as the discriminator to distinguish between `Circle` and `Square`. The function `area` can safely handle the different types based on this property.

---

### 6. **Typeof Type Guard**

The `typeof` operator in TypeScript can be used as a type guard to narrow the type of a variable, especially when working with primitive types like `string`, `number`, `boolean`, etc.

#### Example:

```typescript
function printLength(value: string | number) {
  if (typeof value === "string") {
    console.log(value.length);
  } else {
    console.log(value.toString().length);
  }
}

printLength("Hello");  // Output: 5
printLength(12345);     // Output: 5
```

Here, `typeof` helps to differentiate between `string` and `number` types and appropriately handles each case.

---

### 7. **Type Guards**

Type guards are used in TypeScript to narrow the type of a variable within a specific scope, allowing more precise type checking. They can be created using `typeof`, `instanceof`, or user-defined type guards.

#### Example:

```typescript
function isString(value: unknown): value is string {
  return typeof value === "string";
}

function printString(value: unknown) {
  if (isString(value)) {
    console.log(value.toUpperCase());
  } else {
    console.log("Not a string");
  }
}

printString("Hello");  // Output: HELLO
printString(123);      // Output: Not a string
```

Here, `isString` is a **user-defined type guard**. It returns `true` if the value is a string, and TypeScript narrows the type of `value` within the `if` block.

---

### 8. **Nullable Types / Non-Nullable Types**

In TypeScript, the `null` and `undefined` types are separate, but they can be used in type annotations. You can control whether a type allows `null` or `undefined` using **nullable types**.

#### Example of Nullable Types:

```typescript
let name: string | null = "John";
name = null;  // Valid

let age: number | undefined = 25;
age = undefined;  // Valid
```

#### Example of Non-Nullable Types:

```typescript
let username: string = "Alice";
username = null;  // Error: Type 'null' is not assignable to type 'string'
```

You can use `--strictNullChecks` in TypeScript to enable stricter null checks and avoid assigning `null` or `undefined` to variables unless explicitly allowed.

---

### 9. **Type Assertions**

Type assertions allow you to tell TypeScript to treat a value as a specific type, overriding the inferred type when you're certain of the type of a value.

#### Syntax:

```typescript
let value = "hello" as string;  // Type assertion using 'as'
let numberValue = <number>5;    // Type assertion using '<>'
```

#### Example:

```typescript
const someValue: any = "This is a string";
const stringLength: number = (someValue as string).length;

console.log(stringLength);  // Output: 16
```

Here, `someValue` is treated as a `string` using type assertion so that we can call `length` on it.

---

### 10. **TypeScript Enum**

An **enum** in TypeScript is a way of defining a set of named constants. Enums can be numeric or string-based.

#### Numeric Enum Example:

```typescript
enum Direction {
  Up = 1,
  Down,
  Left,
  Right,
}

let move: Direction = Direction.Up;
console.log(move);  // Output: 1
```

Here, `Direction` is an enum, and each direction has a numeric value associated with it. By default, the first member of an enum is assigned `0`, and subsequent members increment by `1` unless explicitly defined.

#### String Enum Example:

```typescript
enum Status {
  Active = "ACTIVE",
  Inactive = "INACTIVE",
}

let currentStatus: Status = Status.Active;
console.log(currentStatus);  // Output: "ACTIVE"
```

In this example, `Status` is a string enum, and each value is assigned a specific string value.

---

### **Summary**

* **Literal Types**: Allow specifying exact values for variables (`"John"`, `42`, `true`).
* **Union Types**: Allow variables to hold multiple types (`string | number`).
* **Intersection Types**: Combine multiple types into one (`Person & Address`).
* **Instanceof Type Guard**: Narrow the type of a class instance using `instanceof`.
* **Discriminated Unions**: Use a shared property to differentiate between union types (tagged unions).
* **Typeof Type Guard**: Narrow the type of a variable using the `typeof` operator.
* **Type Guards**: Functions that narrow types within specific blocks of code.
* **Nullable Types**: Types that can also hold `null` or `undefined`.
* **Type Assertions**: Used to tell TypeScript to treat a value as a specific type.
* **Enums**: A way to define sets of named constants, either numeric or string-based.

These advanced types help you work with more complex scenarios in TypeScript while maintaining type safety.
