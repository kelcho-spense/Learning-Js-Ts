# Custom Types

In TypeScript, both **Type Aliases** and **Interfaces** allow you to define custom types. While they can sometimes serve the same purpose, there are important differences in their usage and capabilities.

Let's go through each concept in detail with examples:

---

### 1. **Type Aliases**

A **type alias** in TypeScript is a way to define a custom name for any type, whether it's a primitive, union, tuple, or object type.

#### Syntax:

```typescript
type AliasName = Type;
```

#### Example:

```typescript
type Point = {
  x: number;
  y: number;
};

const point: Point = { x: 10, y: 20 };
```

Here, we created a `Point` type alias that represents an object with two properties: `x` and `y`, both of type `number`. This makes the code more readable.

#### Type Aliases for Union and Intersection Types:

You can also use type aliases to create union and intersection types.

**Union Type Example**:

```typescript
type StringOrNumber = string | number;

let value: StringOrNumber;
value = "Hello";  // Valid
value = 10;       // Valid
```

**Intersection Type Example**:

```typescript
type Name = {
  firstName: string;
  lastName: string;
};

type Age = {
  age: number;
};

type Person = Name & Age;

const person: Person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
};
```

---

### 2. **Interfaces in TypeScript**

An **interface** in TypeScript is a way to define a contract for an object or function. It can be used to define the shape of an object, including its properties and their types.

#### Syntax:

```typescript
interface InterfaceName {
  propertyName: PropertyType;
}
```

#### Example:

```typescript
interface Person {
  name: string;
  age: number;
}

const john: Person = {
  name: "John Doe",
  age: 30,
};
```

In this example, the `Person` interface defines that a person object must have a `name` of type `string` and an `age` of type `number`.

---

### 3. **Interface for Function Types**

In TypeScript, you can use interfaces to define the signature of a function, which includes the types of parameters and the return type.

#### Syntax:

```typescript
interface FunctionName {
  (param1: Type1, param2: Type2): ReturnType;
}
```

#### Example:

```typescript
interface AddFunction {
  (a: number, b: number): number;
}

const add: AddFunction = (a, b) => {
  return a + b;
};

console.log(add(5, 10));  // Output: 15
```

In this example, the `AddFunction` interface defines a function type that accepts two `number` arguments and returns a `number`. The `add` function implements that interface.

---

### 4. **Extending Interfaces**

Interfaces in TypeScript can extend other interfaces, meaning you can inherit properties from one interface to create more complex types.

#### Syntax:

```typescript
interface ExtendedInterface extends BaseInterface {
  additionalProperty: Type;
}
```

#### Example:

```typescript
interface Animal {
  name: string;
  sound: string;
}

interface Dog extends Animal {
  breed: string;
}

const myDog: Dog = {
  name: "Buddy",
  sound: "Woof",
  breed: "Golden Retriever",
};
```

In this example:

* The `Dog` interface extends the `Animal` interface, which means it inherits the `name` and `sound` properties.
* The `Dog` interface also adds a new property, `breed`.

---

### 5. **Interface vs Type Alias**

While **interfaces** and **type aliases** can sometimes be used interchangeably, there are differences in their features and usage.

| **Feature**             | **Interface**                                                       | **Type Alias**                                                           |
| ----------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **Declaration Merging** | Yes, interfaces can merge with other interfaces with the same name. | No, type aliases cannot merge.                                           |
| **Extending Types**     | Can extend other interfaces or classes.                             | Can extend other types using `&` (intersection).                         |
| **Use Cases**           | Typically used to define object shapes and class implementations.   | Used for more complex types like unions, tuples, or type compositions.   |
| **Flexibility**         | Less flexible, mainly used for object shapes and functions.         | More flexible, can represent unions, intersections, and primitive types. |

#### Example of Declaration Merging in Interface:

```typescript
interface Car {
  make: string;
  model: string;
}

interface Car {
  year: number;
}

const myCar: Car = {
  make: "Toyota",
  model: "Corolla",
  year: 2021,
};
```

In this example, two `Car` interfaces are declared, and TypeScript automatically merges them, so the `Car` interface ends up with all three properties: `make`, `model`, and `year`.

---

### **When to Use Type Alias vs Interface**

* **Use Interfaces** when:

    * You want to create a contract for object shapes, especially when you need to use **declaration merging**.
    * You are designing objects or classes that need to adhere to a certain structure.
* **Use Type Aliases** when:

    * You need to define **unions**, **intersections**, or **tuples**.
    * You are working with more complex types (e.g., combining different types using `&`, defining a union type, etc.).

**Example** of union and intersection with type alias:

```typescript
type Animal = {
  name: string;
  sound: string;
};

type Mammal = Animal & { hasFur: boolean };  // Intersection type

type Pet = Animal | { isFriendly: boolean }; // Union type

const dog: Mammal = { name: "Dog", sound: "Bark", hasFur: true };
const fish: Pet = { name: "Fish", sound: "Blub" };
```

---

### **Summary**

* **Type Aliases** are useful for defining complex types, such as unions and intersections, or when you want to work with primitive types, tuples, or function signatures.
* **Interfaces** are used to define object structures and class contracts, and they support declaration merging, making them more flexible when it comes to extending types.

Both `interface` and `type alias` are important and can often be used interchangeably, but their use cases and capabilities differ. TypeScript provides these two features to give you more control over your types, ensuring better code clarity and type safety.
