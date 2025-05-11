# Generics

### **Generics in TypeScript**

Generics allow you to define functions, classes, and interfaces with placeholder types, providing greater flexibility and reusability while maintaining type safety. They enable you to work with any data type without sacrificing the type checking TypeScript offers.

---

### **1. What are Generics?**

Generics allow you to define a function, class, or interface with a "type parameter" that can be replaced with different types. You define the type placeholder (usually with `T` or other identifiers), and TypeScript will infer the appropriate type based on the argument you pass into the generic function or class.

#### **Basic Syntax for Generics:**

```ts
function functionName<T>(param: T): T {
  return param;
}
```

Here, `T` is a type parameter, which TypeScript replaces with an actual type when the function is called.

#### **Example - Generic Function:**

```ts
function identity<T>(value: T): T {
  return value;
}

let numberIdentity = identity(10);  // Inferred type is number
let stringIdentity = identity("Hello");  // Inferred type is string

console.log(numberIdentity);  // Output: 10
console.log(stringIdentity);  // Output: Hello
```

In this example, `identity` is a function that returns the value passed to it, and it can work with any type (`T`), whether it's a `string`, `number`, or any other type.

---

### **2. Generic Interfaces**

You can also use generics with interfaces, which makes it possible to define flexible, reusable types.

#### **Syntax:**

```ts
interface GenericInterface<T> {
  value: T;
  getValue(): T;
}
```

#### **Example - Generic Interface:**

```ts
interface Box<T> {
  value: T;
  getValue(): T;
}

const numberBox: Box<number> = {
  value: 42,
  getValue() {
    return this.value;
  },
};

const stringBox: Box<string> = {
  value: "Hello, World!",
  getValue() {
    return this.value;
  },
};

console.log(numberBox.getValue());  // Output: 42
console.log(stringBox.getValue());  // Output: Hello, World!
```

Here, the `Box` interface can accept a type `T` and be used with different types (e.g., `Box<number>` or `Box<string>`).

---

### **3. Generic Classes**

You can also create **generic classes**, which allow you to work with different types of data while keeping everything strongly typed.

#### **Syntax:**

```ts
class ClassName<T> {
  property: T;

  constructor(property: T) {
    this.property = property;
  }

  getProperty(): T {
    return this.property;
  }
}
```

#### **Example - Generic Class:**

```ts
class Container<T> {
  private item: T;

  constructor(item: T) {
    this.item = item;
  }

  getItem(): T {
    return this.item;
  }
}

const numberContainer = new Container<number>(123);
console.log(numberContainer.getItem());  // Output: 123

const stringContainer = new Container<string>("TypeScript");
console.log(stringContainer.getItem());  // Output: TypeScript
```

In this example, `Container` is a generic class that can store any type of item (`T`). It can work with both numbers and strings, maintaining type safety for each.

---

### **4. Generic Constraints**

While generics are flexible, sometimes you may want to restrict the types that can be passed to a generic function, class, or interface. You can use **generic constraints** to ensure that the generic type `T` extends or satisfies a specific type.

#### **Syntax:**

```ts
function functionName<T extends SomeType>(param: T): T {
  // code
}
```

In this example, `T` is constrained to types that extend `SomeType`, meaning only objects of that type (or a subclass of that type) can be used with the function.

#### **Example - Generic Constraint:**

```ts
interface Lengthy {
  length: number;
}

function logLength<T extends Lengthy>(item: T): void {
  console.log(item.length);
}

logLength("Hello");   // Output: 5 (string has a length property)
logLength([1, 2, 3]); // Output: 3 (array has a length property)

// logLength(10);  // Error: Argument of type 'number' is not assignable to parameter of type 'Lengthy'.
```

Here, the `logLength` function is constrained to accept only objects that have a `length` property, such as strings or arrays.

---

### **5. Using Multiple Generics**

You can also define functions, classes, or interfaces that work with multiple generic types.

#### **Syntax:**

```ts
function functionName<T, U>(param1: T, param2: U): T {
  // code
}
```

#### **Example - Multiple Generics:**

```ts
function combine<T, U>(value1: T, value2: U): string {
  return `${value1} and ${value2}`;
}

let combinedString = combine<string, number>("Age", 30);
console.log(combinedString);  // Output: "Age and 30"
```

In this example, `combine` is a function that takes two parameters, `value1` and `value2`, with different types (`T` and `U`), and returns a string.

---

### **6. Using `keyof` with Generics**

You can also use the `keyof` keyword with generics to ensure that the type passed as the argument is a valid key of the object type.

#### **Example - `keyof` with Generics:**

```ts
interface Person {
  name: string;
  age: number;
}

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const person = { name: "John", age: 30 };

let personName = getProperty(person, "name");  // type inferred as string
let personAge = getProperty(person, "age");   // type inferred as number

console.log(personName);  // Output: John
console.log(personAge);   // Output: 30
```

In this example, `K extends keyof T` ensures that `key` must be one of the keys of the object `T`. This ensures that you can't pass an invalid key.

---

### **Summary of Generics and Constraints**

| **Concept**               | **Description**                                                                                       | **Example**                                                  |
| ------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **Basic Generics**        | Functions, classes, and interfaces that work with any type, providing flexibility and type safety.    | `function identity<T>(value: T): T { return value; }`        |
| **Generic Constraints**   | Restrict the types that can be used in a generic function/class to types that extend a specific type. | `function logLength<T extends Lengthy>(item: T): void {}`    |
| **Multiple Generics**     | Functions or classes that take more than one generic type parameter.                                  | `function combine<T, U>(value1: T, value2: U): string {}`    |
| **`keyof` with Generics** | Ensures that a key passed as a generic parameter is a valid key of the type's properties.             | `function getProperty<T, K extends keyof T>(obj: T, key: K)` |

---

### **Conclusion**

Generics in TypeScript allow you to define functions, classes, and interfaces that can work with any type while maintaining strong type safety. With generics, you can create more reusable and flexible code. By applying constraints, you can control the types used in generics, ensuring better type validation and avoiding potential errors.
