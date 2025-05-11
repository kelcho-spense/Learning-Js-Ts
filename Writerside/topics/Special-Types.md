# Special Types

In TypeScript, the `Never`, `Void`, and `Unknown` types are special types that help define the behavior and safety of your code. Here’s a detailed explanation of each type with examples:

### 1. **Never Type**

The `never` type represents values that **never occur**. It's often used in situations where a function never completes or always throws an error, such as a function that never returns or an infinite loop. The `never` type is the **opposite** of `void`, because `void` indicates that a function does not return anything, but `never` indicates that the function **doesn't even return** at all.

#### Characteristics of `never`:

* Functions that always throw an exception or have an infinite loop.
* TypeScript uses `never` for exhaustive checks (e.g., in `switch` statements or condition checks).

**Example**: Using `never` in functions that always throw errors:

```typescript
function throwError(message: string): never {
  throw new Error(message);
}

function infiniteLoop(): never {
  while (true) {
    // Infinite loop
  }
}
```

Here:

* `throwError` always throws an error, so it **never** returns anything.
* `infiniteLoop` runs infinitely and also **never** returns anything.

**Use case**:

* `never` is used when you expect that a function should **never** complete normally (i.e., it never returns).

---

### 2. **Void Type**

The `void` type is typically used for functions that do not return any value. It's often used as the return type of functions that perform side-effects, like logging or updating UI elements, where no value is returned to the caller.

#### Characteristics of `void`:

* Used for functions that don't return a value.
* Typically seen in function signatures.

**Example**: A function returning `void`:

```typescript
function logMessage(message: string): void {
  console.log(message);
}

let result = logMessage("Hello, TypeScript!"); // The result will be `undefined`
console.log(result);  // Output: undefined
```

Here:

* The `logMessage` function performs an action (logging a message) but **does not return a value**. Hence, its return type is `void`.
* The `result` is `undefined`, because `void` functions return nothing.

---

### 3. **Unknown Type**

The `unknown` type is a safer version of `any`. While `any` allows you to assign any type of value to a variable (thereby bypassing TypeScript’s type safety), `unknown` forces you to perform **type-checking** before you can operate on the value.

#### Characteristics of `unknown`:

* You can assign any value to an `unknown` type, but you cannot perform any operations on it until you assert or check its type.
* `unknown` is safer than `any` because it enforces type-checking before performing operations on the value.

**Example**: Using `unknown` type:

```typescript
let value: unknown = 30;

value = "hello";  // Okay to assign a string

// You need to check the type before performing operations
if (typeof value === "string") {
  console.log(value.toUpperCase());  // Works because `value` is confirmed to be a string
}

value = 100;
// value.toFixed();  // Error: Property 'toFixed' does not exist on type 'unknown'.
```

Here:

* `value` can hold any type, but before using it (e.g., calling `toUpperCase`), TypeScript requires you to check the type using a conditional (`typeof` in this case).
* With `unknown`, TypeScript ensures that you don’t accidentally perform operations on a value of an inappropriate type.

**Use case**:

* `unknown` is useful when you want to accept a wide range of possible values but want to maintain safety by requiring the programmer to perform type-checking before using the value.

---

### **Comparison of `never`, `void`, and `unknown`**

| **Type**  | **Description**                                              | **Use Case**                                                                                                 | **Example**                                                                                     |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| `never`   | Represents a value that **never** occurs.                    | Functions that **never return** or run into an infinite loop.                                                | `function throwError(message: string): never { throw new Error(message); }`                     |
| `void`    | Represents the absence of a return value (like `undefined`). | Used for functions that perform an action but **do not return** anything.                                    | `function logMessage(message: string): void { console.log(message); }`                          |
| `unknown` | A safer version of `any`. You must **check** the type first. | Used when you are not sure of the type, but want to ensure safety before performing operations on the value. | `let value: unknown = 30; if (typeof value === "string") { console.log(value.toUpperCase()); }` |

---