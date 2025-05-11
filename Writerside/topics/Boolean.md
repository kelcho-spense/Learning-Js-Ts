# Boolean

### Boolean Data Type in TypeScript

The **Boolean** data type in TypeScript represents a logical entity that can have one of two possible values: `true` or `false`. These values are used to represent truth values in conditions, such as in control flow (if-else statements, loops, etc.).

#### Characteristics of the Boolean Data Type:

* **Type:** Boolean is a primitive type, and it can only have two values: `true` or `false`.
* **Usage:** It is widely used in conditional statements, expressions, and as flags in applications to control behavior or represent binary state.

### 1. **Creating Boolean Variables**

You can declare and initialize a Boolean variable using either a boolean literal (`true` or `false`) or a Boolean constructor.

#### Example 1: Boolean Literal

```typescript
let isActive: boolean = true;
let isCompleted: boolean = false;

console.log(isActive);      // Output: true
console.log(isCompleted);   // Output: false
```

#### Example 2: Using the `Boolean` Constructor

```typescript
let isVerified: boolean = Boolean(1);  // Non-zero values are converted to true
let isEmpty: boolean = Boolean(0);     // Zero is converted to false

console.log(isVerified); // Output: true
console.log(isEmpty);    // Output: false
```

In the above example:

* `Boolean(1)` converts to `true` because any non-zero number is truthy.
* `Boolean(0)` converts to `false` because `0` is falsy.

### 2. **Boolean Expressions**

Boolean values are often the result of expressions that compare two values or evaluate conditions. These expressions evaluate to either `true` or `false`.

#### Comparison Operators:

* `==` (Equal to)
* `!=` (Not equal to)
* `>` (Greater than)
* `<` (Less than)
* `>=` (Greater than or equal to)
* `<=` (Less than or equal to)

#### Example:

```typescript
let a: number = 10;
let b: number = 20;

let result: boolean = a < b;  // Evaluates to true because 10 is less than 20
console.log(result);          // Output: true
```

### 3. **Boolean in Conditional Statements**

Boolean values are most commonly used in control flow statements like **if**, **while**, or **for** loops to check whether a condition is true or false.

#### Example 1: `if` Statement

```typescript
let isLoggedIn: boolean = true;

if (isLoggedIn) {
    console.log("Welcome back!");
} else {
    console.log("Please log in.");
}
// Output: Welcome back!
```

#### Example 2: `while` Loop

```typescript
let count: number = 5;

while (count > 0) {
    console.log(count);
    count--;
}
// Output: 5, 4, 3, 2, 1
```

### 4. **Boolean Coercion (Truthy and Falsy Values)**

In JavaScript (and TypeScript), values other than `false`, `0`, `NaN`, `""` (empty string), `null`, and `undefined` are treated as **truthy**. These can be coerced into `true` when used in a Boolean context.

* **Truthy:** Non-zero numbers, non-empty strings, objects, arrays, etc.
* **Falsy:** `false`, `0`, `""`, `null`, `undefined`, `NaN`.

#### Example:

```typescript
let truthyValue: boolean = Boolean("Hello");  // Non-empty string is truthy
let falsyValue: boolean = Boolean(0);         // Zero is falsy

console.log(truthyValue);  // Output: true
console.log(falsyValue);   // Output: false
```

### 5. **Using Boolean in Logical Operations**

You can use logical operators to combine Boolean values:

* `&&` (AND)
* `||` (OR)
* `!` (NOT)

#### Example 1: Logical AND (`&&`)

```typescript
let a: boolean = true;
let b: boolean = false;

let result: boolean = a && b; // Logical AND
console.log(result);  // Output: false
```

In this case, the result is `false` because both conditions need to be `true` for the `AND` operator to return `true`.

#### Example 2: Logical OR (`||`)

```typescript
let a: boolean = true;
let b: boolean = false;

let result: boolean = a || b; // Logical OR
console.log(result);  // Output: true
```

In this case, the result is `true` because at least one condition must be `true` for the `OR` operator to return `true`.

#### Example 3: Logical NOT (`!`)

```typescript
let a: boolean = true;
let b: boolean = false;

console.log(!a);  // Output: false (Negation of `true`)
console.log(!b);  // Output: true (Negation of `false`)
```

### 6. **Boolean as Flags**

A **Boolean flag** is a variable that is used to indicate the state of something, such as whether a process is complete or whether an action should be performed.

#### Example:

```typescript
let isUserAuthenticated: boolean = false;

// Simulate login process
function login(username: string, password: string) {
    if (username === "admin" && password === "password123") {
        isUserAuthenticated = true;  // User is authenticated
    }
}

login("admin", "password123");

if (isUserAuthenticated) {
    console.log("User has logged in successfully.");
} else {
    console.log("Invalid credentials.");
}
// Output: User has logged in successfully.
```

### 7. **Boolean Data Type in TypeScript Type Annotations**

In TypeScript, you can explicitly specify that a variable is of the `boolean` type using type annotations. This ensures that only `true` or `false` values can be assigned to the variable.

#### Example:

```typescript
let isActive: boolean = true;  // Boolean type annotation

isActive = false;  // This is valid
isActive = "yes";   // Error: Type 'string' is not assignable to type 'boolean'.
```

---

### 8. **Boolean and TypeScript's Type Inference**

TypeScript automatically infers the type of a variable based on its initial value, so you can omit the type annotation if you assign a `boolean` value.

#### Example:

```typescript
let isOpen = true;  // TypeScript infers `isOpen` as a boolean type

isOpen = false;     // Valid
isOpen = 1;         // Error: Type 'number' is not assignable to type 'boolean'.
```

---

### Summary of Boolean Data Type in TypeScript:

| **Feature**                | **Description**                                                                                                        | **Example**                                   |                        |                        |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------- | --------------------------------------------- | ---------------------- | ---------------------- |
| **Boolean Values**         | Can only have two values: `true` or `false`.                                                                           | `let isCompleted: boolean = true;`            |                        |                        |
| **Boolean Operations**     | Logical operations with `&&`, \`                                                                                       |                                               | `, and `!\` operators. | `let result = a && b;` |
| **Conditional Statements** | Used in `if`, `while`, `for`, and other conditional statements to control flow.                                        | `if (isActive) { console.log("Active"); }`    |                        |                        |
| **Type Annotation**        | Explicitly declaring a variable as `boolean`.                                                                          | `let isLoggedIn: boolean = false;`            |                        |                        |
| **Boolean Coercion**       | Any non-falsy value (e.g., `1`, `"string"`, `[]`) is coerced to `true`, while falsy values (`0`, `""`) become `false`. | `Boolean(0); // false`, `Boolean(1); // true` |                        |                        |
| **Flags**                  | Commonly used as flags to indicate binary states.                                                                      | `let isUserAuthenticated: boolean = true;`    |                        |                        |

In conclusion, the **Boolean** data type is crucial for controlling logic in TypeScript, and it provides a simple but powerful mechanism for handling binary conditions and flags. Understanding how to use `true` and `false` effectively, along with logical operators and conditional statements, will help you write efficient and readable TypeScript code.
