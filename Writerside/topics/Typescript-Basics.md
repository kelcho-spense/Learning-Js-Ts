# Typescript Basics

Typescript Types (or data types) bring static type checking into the dynamic world of Javascript.
## What is a Data Type?
The Type or the Data Type is an attribute of data that tells us what kind of value the data has. Whether it is a `number`, `string`, `boolean`, etc. The type of data defines the operations that we can do on that data.
## Typescript Data Types
JavaScript has eight data types. `Seven` primitive types and one object Data type. The primitive types are `number`, `string`, `boolean`, `bigint`, `symbol`, `undefined`, and null. Everything else is an `object` in JavaScript.

> The TypeScript Type System supports all of them and also brings its own special types. They are `unknown`, `any`, `void` & `never`. TypeScript also provides both numeric and string-based `enums`. Enums allow a developer to define a set of named constants

The following diagram shows the relationship between various types.

![image_8.png](image_8.png)

Sure! Here's a detailed set of notes on the topics you requested, along with examples to help you understand each concept:

---

## 1. **TypeScript Data Types**

In TypeScript, variables are assigned types to enforce type safety. These types can be basic types like numbers and strings, or more complex types like arrays and objects.

### Basic Data Types:

* **number**: Represents both integer and floating-point numbers.
* **string**: Represents text values.
* **boolean**: Represents `true` or `false`.
* **null**: Represents a null value (intentional absence of any object value).
* **undefined**: Represents an undefined value (a variable that has been declared but not assigned a value).
* **void**: Used when there is no return value for a function.

#### Example:

```typescript
let age: number = 25;
let name: string = "Alice";
let isActive: boolean = true;
let nothing: null = null;
let undefinedValue: undefined = undefined;
```

---

## 2. **Type Annotations**

Type annotations in TypeScript are used to explicitly specify the type of a variable, function parameter, or return type. Type annotations help TypeScript enforce the correct type for variables and functions.

### Syntax:

```typescript
let variableName: type = value;
```

#### Example:

```typescript
let message: string = "Hello, TypeScript!";
let count: number = 10;
```

In this example, `message` is annotated as a `string`, and `count` is annotated as a `number`. This helps TypeScript enforce that only values of these types can be assigned to these variables.

---

## 3. **Variable Declaration**

In TypeScript, you can declare variables using the `let`, `const`, and `var` keywords.

### `let`:

* Used to declare a block-scoped variable.
* The value of `let`-declared variables can be changed.

### `const`:

* Used to declare a block-scoped, read-only constant.
* The value of a `const` variable cannot be changed after initialization.

### `var`:

* **Function-scoped** variable declaration (more common in JavaScript).
* It is less commonly used in TypeScript since `let` and `const` are more predictable.

#### Example:

```typescript
let age: number = 30; // Variable with let
const birthYear: number = 1991; // Constant with const
var city: string = "New York"; // Function-scoped variable with var
```

---

## 4. **Identifiers & Keywords**

* **Identifiers** are the names given to variables, functions, classes, etc. In TypeScript, an identifier can contain letters, digits, underscores, and dollar signs, but it cannot begin with a digit.

* **Keywords** are reserved words that have a special meaning in TypeScript and cannot be used as identifiers. For example, `let`, `const`, `return`, `if`, `else`, `class`, `function`, etc.

#### Example:

```typescript
let personName: string = "John"; // "personName" is an identifier
const myClass: string = "Math"; // "myClass" is an identifier

// Keywords cannot be used as identifiers:
let if = 5; // Error: "if" is a keyword
```

---

## 5. **Variable Scope**

In TypeScript, the **scope** of a variable determines where the variable can be accessed. The scope is determined by where the variable is declared (within a function, a block, etc.).

### Types of Scopes:

* **Global Scope**: A variable declared outside any function or block is accessible anywhere in the program.
* **Function Scope**: Variables declared inside a function are only accessible within that function.
* **Block Scope**: Variables declared with `let` and `const` inside a block (`{}`) are only accessible within that block.

#### Example:

```typescript
let globalVar: string = "I'm global";

function testScope() {
  let functionVar: string = "I'm local to the function";
  console.log(globalVar);  // Accessible
  console.log(functionVar); // Accessible
}

console.log(globalVar); // Accessible
// console.log(functionVar); // Error: functionVar is not defined outside the function
```

---

## 6. **Let, Var & Const**

### **let**:

* Block-scoped.
* Can be reassigned.

### **const**:

* Block-scoped.
* Cannot be reassigned after initialization.

### **var**:

* Function-scoped.
* Can be reassigned.
* Can lead to issues like hoisting and scope leakage, so it's best to avoid `var` in modern TypeScript code.

#### Example:

```typescript
let number = 10;
number = 20;  // Valid

const constantValue = 30;
constantValue = 40; // Error: Assignment to constant variable.

var oldVariable = "Hello";
oldVariable = "World";  // Valid
```

---

## 7. **Constants**

Constants are variables whose value cannot be changed after initialization. In TypeScript, constants are declared with the `const` keyword. Constants must always be initialized at the time of declaration.

#### Example:

```typescript
const PI: number = 3.14;
PI = 3.14159; // Error: Cannot assign to 'PI' because it is a constant
```

---

## 8. **Type Inference**

TypeScript can automatically infer the type of a variable based on the assigned value. If you don't explicitly annotate a variable, TypeScript will infer the type for you.

#### Example:

```typescript
let number = 5;  // TypeScript infers 'number'
let message = "Hello";  // TypeScript infers 'string'
```

Even though the variables are not annotated with types, TypeScript knows the type because of the assigned value.

---

## 9. **Any Type**

The `any` type in TypeScript allows a variable to hold any value. It effectively disables type checking for that variable, making it behave like a plain JavaScript variable.

While `any` is useful in some cases (e.g., when dealing with dynamic content or external libraries), it should be used sparingly, as it undermines the benefits of type safety in TypeScript.

#### Example:

```typescript
let anything: any = 5;
anything = "Hello";  // Valid
anything = true;     // Valid
```

---

## 10. **Strings**

Strings in TypeScript work the same way as in JavaScript. A string can be enclosed in either single quotes, double quotes, or backticks (for template literals).

### Template Literals:

Template literals allow embedding expressions within string literals, using `${}` syntax.

#### Example:

```typescript
let name: string = "Alice";
let greeting: string = `Hello, ${name}!`; // Template literal
console.log(greeting); // Outputs: Hello, Alice!
```

You can also perform string concatenation using the `+` operator:

```typescript
let part1: string = "Hello, ";
let part2: string = "World!";
let combined: string = part1 + part2; // Concatenation
console.log(combined);  // Outputs: Hello, World!
```

---
