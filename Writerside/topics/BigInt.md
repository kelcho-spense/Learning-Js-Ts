# BigInt

### BigInt Data Type in TypeScript

The **`BigInt`** data type was introduced to JavaScript and TypeScript to allow representation of **arbitrary-precision integers**. While the regular `number` type in JavaScript/TypeScript can represent integers up to **2^53 - 1** (`Number.MAX_SAFE_INTEGER`), `BigInt` can handle integers much larger than this, or even smaller than `Number.MIN_SAFE_INTEGER`.

### Key Characteristics of BigInt:

* **Arbitrary-Precision**: Unlike the `number` type which is limited to **double-precision floating point format**, `BigInt` can handle integers of arbitrary size, which means you can work with very large or very small integers beyond the safe limits of `number`.
* **Syntax**: A `BigInt` is created by appending an `n` to the end of an integer literal. For example, `1234567890123456789012345678901234567890n`.

### 1. **Creating BigInt**

You can create a `BigInt` in two ways:

1. **Using the `n` suffix** (recommended):

   ```typescript
   let bigNum: BigInt = 1234567890123456789012345678901234567890n;
   console.log(bigNum);  // Output: 1234567890123456789012345678901234567890n
   ```

2. **Using the `BigInt()` constructor**:

   ```typescript
   let bigNum: BigInt = BigInt("1234567890123456789012345678901234567890");
   console.log(bigNum);  // Output: 1234567890123456789012345678901234567890n
   ```

    * The `BigInt()` constructor accepts a string that represents the integer.
    * You cannot directly pass a floating-point number or a non-numeric string.

---

### 2. **Operations with BigInt**

You can perform basic arithmetic operations such as addition, subtraction, multiplication, division, and exponentiation with `BigInt`.

#### Example:

```typescript
let num1: BigInt = 1234567890123456789012345678901234567890n;
let num2: BigInt = 9876543210987654321098765432109876543210n;

let sum: BigInt = num1 + num2;
let difference: BigInt = num2 - num1;
let product: BigInt = num1 * num2;
let quotient: BigInt = num2 / num1;

console.log(sum);        // Output: 11111111101111111110111111111011111111100n
console.log(difference); // Output: 8641975320864197532086429753208641975320n
console.log(product);    // Output: 121932631137021795226186647069939035392315418531801907245933536542406477279031453736177535709258073310000n
console.log(quotient);   // Output: 8n
```

**Note**: Operations with `BigInt` return values of type `BigInt`.

---

### 3. **BigInt and Comparison**

You can compare `BigInt` values using comparison operators such as `<`, `>`, `<=`, `>=`, `===`, and `!==`.

#### Example:

```typescript
let num1: BigInt = 1000n;
let num2: BigInt = 500n;

console.log(num1 > num2);   // Output: true
console.log(num1 === num2); // Output: false
```

### 4. **BigInt and Type Safety**

`BigInt` is not directly compatible with the `number` type, meaning that you cannot mix `BigInt` and `number` values in arithmetic operations.

For example:

```typescript
let num: number = 10;
let bigNum: BigInt = 1000n;

console.log(num + bigNum); // Error: Cannot mix BigInt and other types
```

To resolve this, you would need to explicitly convert one type to the other, which is not always recommended unless you are sure about your logic.

---

### BigInt vs. Number

Although `BigInt` offers significant advantages in terms of handling large integers, there are key differences between `BigInt` and `number`:

| **Feature**       | **BigInt**                                                               | **Number**                                                                   |
| ----------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| **Size**          | Can represent arbitrarily large integers.                                | Limited to **2^53 - 1** for integers.                                        |
| **Type**          | Used specifically for large integers.                                    | Can represent both integers and floating-point numbers.                      |
| **Precision**     | Supports exact precision for large integers.                             | Limited precision due to floating-point representation (IEEE 754).           |
| **Operations**    | Supports arithmetic operations but only with other `BigInt`s.            | Supports both integers and floating-point numbers, and operations with both. |
| **Syntax**        | Created with `n` suffix or `BigInt()` constructor.                       | Normal numbers written directly (e.g., `123.45`, `100`).                     |
| **Compatibility** | Cannot be mixed with `number` in operations without explicit conversion. | Can easily be mixed with other `number` types in arithmetic.                 |
| **Use Case**      | Use when working with large integers or arbitrary precision.             | Use for typical numbers (integers and floating-point).                       |

#### Example: BigInt vs. Number

```typescript
let bigIntVal: BigInt = 1234567890123456789012345678901234567890n;
let numberVal: number = 1234567890123456789012345678901234567890;

console.log(typeof bigIntVal);  // Output: bigint
console.log(typeof numberVal);  // Output: number

// BigInt and number cannot be mixed directly:
console.log(bigIntVal + numberVal); // Error: Cannot mix BigInt and other types.
```

To work with a `BigInt` and `number` together, you can convert one to the other explicitly, but it's generally not recommended because it might cause precision issues or other errors.

---

### 5. **When to Use BigInt**

* **Large Numbers**: Use `BigInt` when you need to work with numbers beyond the limit of `Number.MAX_SAFE_INTEGER` (i.e., larger than **2^53 - 1**).
* **Cryptography**: For cryptographic algorithms or applications involving very large prime numbers, `BigInt` is a suitable choice.
* **High Precision Calculations**: If your application requires high precision for very large integers, `BigInt` is ideal.

### 6. **Limitations of BigInt**

* **Performance**: `BigInt` operations might be slower than `number` operations, especially for smaller values.
* **No Floating-Point Support**: `BigInt` cannot be used with floating-point numbers. If you need to work with both integers and floating-point values, you will need to use `number` for floating-point operations.
* **No Implicit Type Conversion**: TypeScript will not automatically convert between `BigInt` and `number`, which means you'll need to handle the type conversion manually.

---

### Summary of Key Differences Between `BigInt` and `Number`

| **Aspect**                | **BigInt**                           | **Number**                                                  |
| ------------------------- | ------------------------------------ | ----------------------------------------------------------- |
| **Size Limit**            | Arbitrary precision                  | Limited to 2^53 - 1 for integers                            |
| **Floating Point**        | No floating-point support            | Supports both integers and floating-point numbers           |
| **Use Case**              | Large integers, exact precision      | General-purpose numbers                                     |
| **Syntax**                | `123456789n`, `BigInt()` constructor | `123`, `123.45`                                             |
| **Arithmetic with Types** | Only with other `BigInt` types       | Can work with both `number` and `BigInt` (after conversion) |
| **Mixing Types**          | Cannot mix with `number`             | Can mix with `number` in operations                         |

In conclusion, **`BigInt`** is an excellent choice for working with large integers or when exact precision is required. However, if you don’t need to work with very large numbers and need to handle both integers and floating-point numbers, **`number`** might be more efficient and flexible.
