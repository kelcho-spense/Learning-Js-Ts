# Numbers

Sure! Here's a detailed explanation of **Number** data types in TypeScript, including concepts like **NaN**, **Min/Max values**, **EPSILON**, **Floating Point Precision**, and **Infinity**, with examples to help you understand each topic.

---

### 1. **Number Data Type in TypeScript**

The **`number`** data type in TypeScript is used to represent numeric values, including both integers and floating-point numbers. This is similar to JavaScript’s `number` type, which can hold integers, floating-point numbers, or even special values like **`NaN`**, **`Infinity`**, and **`-Infinity`**.

TypeScript provides support for the following types of numbers:

* **Integers**: Whole numbers (e.g., `10`, `-5`, `200`).
* **Floating Point Numbers**: Decimal numbers (e.g., `3.14`, `-0.5`, `100.75`).

#### Example:

```typescript
let integer: number = 42;
let floatingPoint: number = 3.14159;
console.log(integer);       // Output: 42
console.log(floatingPoint); // Output: 3.14159
```

---

### 2. **NaN in TypeScript**

**`NaN`** stands for **Not-a-Number**. It is a special numeric value that indicates an operation that cannot produce a valid number. For example, dividing zero by zero or attempting to convert a non-numeric string to a number results in `NaN`.

#### Characteristics:

* `NaN` is **not equal to any value**, including itself.
* It is a way to represent an undefined or unrepresentable value in numeric calculations.

#### Example:

```typescript
let result: number = 0 / 0;  // This will produce NaN
console.log(result);         // Output: NaN

let invalidNumber: number = Number("hello");
console.log(invalidNumber);  // Output: NaN
console.log(isNaN(invalidNumber)); // Output: true
```

In the example above:

* `0 / 0` results in `NaN`.
* `Number("hello")` results in `NaN` since "hello" is not a valid number.

#### Checking `NaN`:

You can check if a value is `NaN` using the `isNaN()` function or the `Number.isNaN()` function.

```typescript
let value: number = NaN;
console.log(isNaN(value));  // Output: true
console.log(Number.isNaN(value));  // Output: true
```

---

### 3. **Min, Max & Safe Values in TypeScript**

TypeScript uses the same numeric limits as JavaScript, which are defined in **`Number.MIN_VALUE`**, **`Number.MAX_VALUE`**, and **`Number.MAX_SAFE_INTEGER`**.

* **`Number.MIN_VALUE`**: The smallest positive number (greater than 0).
* **`Number.MAX_VALUE`**: The largest representable number.
* **`Number.MAX_SAFE_INTEGER`**: The largest integer that can be represented safely in JavaScript/TypeScript without precision loss.
* **`Number.MIN_SAFE_INTEGER`**: The smallest safe integer.

#### Example:

```typescript
console.log(Number.MIN_VALUE);        // Output: 5e-324 (smallest positive number)
console.log(Number.MAX_VALUE);        // Output: 1.7976931348623157e+308 (largest number)
console.log(Number.MAX_SAFE_INTEGER); // Output: 9007199254740991 (largest safe integer)
console.log(Number.MIN_SAFE_INTEGER); // Output: -9007199254740991 (smallest safe integer)
```

These constants can be used to check if a number exceeds the representable limits in TypeScript.

---

### 4. **EPSILON & Floating Point Precision**

**`Number.EPSILON`** represents the smallest difference between two representable numbers in JavaScript/TypeScript. It is useful for handling precision issues when dealing with floating-point numbers.

Floating-point numbers in JavaScript and TypeScript can sometimes lead to precision issues due to the way they are stored in binary format.

#### Example:

```typescript
let a: number = 0.1 + 0.2;
let b: number = 0.3;

console.log(a === b);  // Output: false (due to floating-point precision issues)
```

This happens because `0.1 + 0.2` does not result exactly in `0.3` due to floating-point precision issues.

To check if two floating-point numbers are effectively the same (considering precision), you can use `Number.EPSILON`:

```typescript
let a: number = 0.1 + 0.2;
let b: number = 0.3;

console.log(Math.abs(a - b) < Number.EPSILON);  // Output: true
```

Here, we use `Math.abs(a - b) < Number.EPSILON` to check if the difference between `a` and `b` is smaller than the smallest possible difference.

---

### 5. **Infinity in TypeScript**

**`Infinity`** represents the mathematical infinity. It is a special numeric value that is larger than all finite numbers. **`-Infinity`** is the counterpart that represents negative infinity.

* **Positive Infinity**: `Infinity`
* **Negative Infinity**: `-Infinity`

You can get `Infinity` by dividing a positive number by zero and `-Infinity` by dividing a negative number by zero.

#### Example:

```typescript
let posInfinity: number = 1 / 0;
let negInfinity: number = -1 / 0;

console.log(posInfinity);  // Output: Infinity
console.log(negInfinity);  // Output: -Infinity

console.log(1 / Infinity);  // Output: 0 (smallest representable number)
console.log(-1 / Infinity); // Output: -0 (negative smallest representable number)
```

---

### Summary of Key Concepts:

| **Concept**             | **Description**                                                                                                                               | **Example**                                            |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **NaN (Not-a-Number)**  | Represents an invalid number or a calculation that cannot produce a valid number (e.g., `0 / 0` or `Number("text")`).                         | `let result = 0 / 0;` `console.log(result);`           |
| **Min & Max Values**    | **`Number.MIN_VALUE`** is the smallest positive number. **`Number.MAX_VALUE`** is the largest possible number.                                | `console.log(Number.MAX_VALUE);`                       |
| **Safe Values**         | **`Number.MAX_SAFE_INTEGER`** is the largest safe integer without precision loss. **`Number.MIN_SAFE_INTEGER`** is the smallest safe integer. | `console.log(Number.MAX_SAFE_INTEGER);`                |
| **EPSILON & Precision** | **`Number.EPSILON`** is the smallest difference between two representable numbers. Helps manage floating-point precision errors.              | `Math.abs(a - b) < Number.EPSILON`                     |
| **Infinity**            | Represents positive and negative infinity. **`Infinity`** is larger than any number, and **`-Infinity`** is smaller than any number.          | `let posInfinity = 1 / 0;` `console.log(posInfinity);` |

---
