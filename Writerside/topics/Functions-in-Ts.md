# Functions in Ts


In TypeScript, functions are defined using the `function` keyword. Type annotations are used to specify types for function parameters and return values, ensuring type safety.

### Basic Syntax

```ts
function functionName(parameters: type): returnType {
  // code to be executed
}
```

### Example

```ts
function myFunction(a: number, b: number): number {
  return a * b;
}
```

In this example, both `a` and `b` are explicitly typed as `number`, and the return type is also `number`.

---

### Function Hoisting

Hoisting is JavaScript's default behavior where declarations are moved to the top of their scope. This applies to both variable and function declarations.

In TypeScript, function declarations are hoisted, allowing you to call the function before its definition.

Example:

```ts
myFunction(5);

function myFunction(y: number): number {
  return y * y;
}
```

In this case, `myFunction` is called before its definition, but TypeScript ensures that the function is correctly typed and hoisted.

---

### Function Parameters and Arguments

In TypeScript, function `parameters` are the names listed in the function definition, and function `arguments` are the actual values passed to (and received by) the function.

Syntax:

```ts
function functionName(parameter1: type, parameter2: type, parameter3: type): returnType {
  // code to be executed
}
```

---

### Default Parameter Values

You can assign default values to function parameters in TypeScript. If a parameter is not passed, the default value will be used.

Example:

```ts
function myFunction(x: number, y: number = 10): number {
  return x + y;
}

myFunction(5); // y defaults to 10
```

In this example, if `y` is not provided, it will default to `10`.

---

## Types of Function

### Arrow Functions

Arrow functions provide a concise syntax for writing function expressions. In TypeScript, you can define types for the parameters and the return type of an arrow function.

```ts
// ES5
let x = function(x: number, y: number): number {
  return x * y;
}

// ES6 (Arrow function)
const x = (x: number, y: number): number => x * y;
```

In the ES6 version, the `function` keyword is omitted, and the return type is inferred or explicitly defined. The parameter types (`x` and `y`) are explicitly typed as `number`.

---

### Immediately Invoked Function Expressions (IIFE)

In TypeScript, Immediately Invoked Function Expressions (IIFE) can be defined as follows. An IIFE is a function that is invoked immediately after being defined.

Syntax:

```ts
(function() {
  // statements
})()
```

Example:

```ts
(function () {
  let x: string = "Hello!!"; // I will invoke myself
})();
```

In this example, the IIFE runs immediately after being defined. The variable `x` is typed as a `string` to maintain type safety.

---

This version uses TypeScript’s strong typing to ensure that function parameters and return types are explicit, which provides better code validation and prevents type-related errors.
