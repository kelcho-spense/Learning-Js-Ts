# Typescript Operators

Here’s a more **strongly typed** approach to explaining **TypeScript Operators** with proper types and detailed examples for each:

---

### **1. Arithmetic Operators**

Arithmetic operators are used to perform mathematical calculations, such as addition, subtraction, multiplication, etc.

#### Types: {id="types_1"}

* **Operand Types**: `number`
* **Return Type**: `number`

#### Example: {id="example_1"}

```typescript
let x: number = 5;
let y: number = 3;

let sum: number = x + y;        // Addition
let diff: number = x - y;       // Subtraction
let prod: number = x * y;       // Multiplication
let quotient: number = x / y;   // Division
let remainder: number = x % y;  // Modulus (Remainder)
let power: number = x ** y;     // Exponentiation

console.log(sum, diff, prod, quotient, remainder, power);
```

---

### **2. Unary Plus / Unary Minus Operators**

These operators are used to convert a variable to a number and to negate a number.

#### Types: {id="types_2"}

* **Unary Plus (`+`)**: Converts `string` or `boolean` to `number`.
* **Unary Minus (`-`)**: Negates a `number`.

#### Example: {id="example_2"}

```typescript
let str: string = "5";
let num: number = +str;         // Converts string "5" to number 5

let positive: number = 5;
let negative: number = -positive; // Negates value to -5

console.log(num, negative);
```

---

### **3. Increment/Decrement Operators**

These operators are used to increase or decrease a variable’s value by `1`.

#### Types: {id="types_3"}

* **Operand Type**: `number`
* **Return Type**: `number`

#### Example: {id="example_3"}

```typescript
let count: number = 0;

count++;  // Post-increment, first returns count, then increments
console.log(count);  // Output: 1

++count;  // Pre-increment, increments count, then returns it
console.log(count);  // Output: 2

count--;  // Post-decrement, first returns count, then decrements
console.log(count);  // Output: 1

--count;  // Pre-decrement, decrements count, then returns it
console.log(count);  // Output: 0
```

---

### **4. Comparison / Relational Operators**

These operators are used to compare two values.

#### Types: {id="types_4"}

* **Operand Types**: `number`, `string`, `boolean`, `object`, etc.
* **Return Type**: `boolean`

#### Example: {id="example_4"}

```typescript
let a: number = 10;
let b: number = 5;

let isGreaterThan: boolean = a > b;   // Greater than
let isLessThan: boolean = a < b;      // Less than
let isEqualTo: boolean = a == b;      // Loose equality
let isNotEqual: boolean = a != b;     // Loose inequality

console.log(isGreaterThan, isLessThan, isEqualTo, isNotEqual);
```

---

### **5. Equality / Strict Equality Operators**

These operators check for value and type equality.

#### Types: {id="types_5"}

* **Operand Types**: `number`, `string`, `boolean`, `object`, etc.
* **Return Type**: `boolean`

#### Example:

```typescript
let num1: number = 5;
let num2: string = "5";

let looseEquality: boolean = num1 == num2;   // Loose equality
let strictEquality: boolean = num1 === num2;  // Strict equality

console.log(looseEquality, strictEquality);  // Output: true, false
```

---

### **6. Ternary Conditional Operator**

The ternary operator provides a shorthand for an `if-else` statement.

#### Types: {id="types_6"}

* **Operand Types**: `boolean`
* **Return Type**: Depends on the expressions

#### Example: {id="example_5"}

```typescript
let age: number = 18;

let result: string = age >= 18 ? "Adult" : "Minor";

console.log(result);  // Output: Adult
```

---

### **7. Logical Operators**

Logical operators are used to perform logical operations on boolean values.

#### Types:

* **Operand Types**: `boolean`
* **Return Type**: `boolean`

#### Example:

```typescript
let x: boolean = true;
let y: boolean = false;

let andResult: boolean = x && y;    // AND
let orResult: boolean = x || y;     // OR
let notResult: boolean = !x;        // NOT

console.log(andResult, orResult, notResult);  // Output: false, true, false
```

---

### **8. Bitwise Operators**

Bitwise operators operate on binary representations of numbers.

#### Types:

* **Operand Types**: `number`
* **Return Type**: `number`

#### Example:

```typescript
let a: number = 5;  // Binary: 0101
let b: number = 3;  // Binary: 0011

let andResult: number = a & b;    // AND: 0101 & 0011 = 0001
let orResult: number = a | b;     // OR: 0101 | 0011 = 0111
let xorResult: number = a ^ b;    // XOR: 0101 ^ 0011 = 0110
let notResult: number = ~a;       // NOT: ~0101 = 1010

console.log(andResult, orResult, xorResult, notResult);
```

---

### **9. Assignment Operators**

Assignment operators are used to assign values to variables.

#### Types:

* **Operand Types**: `number`, `string`, `boolean`, etc.
* **Return Type**: `number` (or whatever type the left operand is)

#### Example:

```typescript
let x: number = 5;

x += 3;  // x = x + 3
x -= 2;  // x = x - 2
x *= 4;  // x = x * 4
x /= 2;  // x = x / 2
x %= 3;  // x = x % 3

console.log(x);  // Output: 2 (5 + 3 - 2 * 4 / 2 % 3)
```

---

### **10. Nullish Coalescing Operator (`??`)**

The nullish coalescing operator returns the right operand when the left operand is `null` or `undefined`.

#### Types:

* **Operand Types**: `null`, `undefined`, or any type.
* **Return Type**: The type of the right operand.

#### Example:

```typescript
let name: string | null = null;
let defaultName: string = "Guest";

let userName: string = name ?? defaultName;

console.log(userName);  // Output: Guest (because name is null)
```

---

### **11. Comma Operator (`,`)**

The comma operator allows multiple expressions to be evaluated from left to right, and the result of the last expression is returned.

#### Types:

* **Operand Types**: Any valid expression.
* **Return Type**: The type of the last expression evaluated.

#### Example:

```typescript
let a: number = 5;
let b: number = 10;

let result: number = (a++, b++, a + b);

console.log(result);  // Output: 21 (last expression: 6 + 10)
```

---

### **12. Operator Precedence**

Operator precedence defines the order in which operators are evaluated in an expression.

#### Example:

```typescript
let result1: number = 2 + 3 * 4; // Multiplication has higher precedence
console.log(result1);  // Output: 14 (2 + (3 * 4))

let result2: number = (2 + 3) * 4; // Parentheses change precedence
console.log(result2);  // Output: 20 ((2 + 3) * 4)
```

---

### **Conclusion**

* **Arithmetic Operators**: Perform basic math operations (`+`, `-`, `*`, `/`, `%`).
* **Unary Operators**: Convert values to numbers or negate them (`+`, `-`).
* **Increment/Decrement Operators**: Increase or decrease by 1 (`++`, `--`).
* **Comparison Operators**: Compare values (`>`, `<`, `==`, `===`, etc.).
* **Ternary Operator**: Shortened `if-else` syntax.
* **Logical Operators**: Perform logical operations (`&&`, `||`, `!`).
* **Bitwise Operators**: Operate on binary numbers (`&`, `|`, `^`, `<<`, `>>`).
* **Assignment Operators**: Assign and perform operations (`=`, `+=`, `-=`, etc.).
* **Nullish Coalescing**: Returns the right operand if the left is `null` or `undefined`.
* **Comma Operator**: Evaluates multiple expressions and returns the result of the last one.
* **Operator Precedence**: Determines the order in which operations are evaluated.

Each operator is essential for performing operations on values, and understanding the types involved ensures type safety and proper use of these operators in TypeScript.
