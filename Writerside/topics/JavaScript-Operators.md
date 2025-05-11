# JavaScript Operators

Javascript operators are used to perform different types of mathematical and logical computations.
Examples:
* The Assignment Operator `=` assigns values
* The Addition Operator `+` adds values
* The Multiplication Operator `*` multiplies values
* The Comparison Operator `>` compares values

## JavaScript Assignment
The **Assignment** Operator (=) assigns a value to a variable:
```js
// Assign the value 5 to x
let x = 5;
// Assign the value 2 to y
let y = 2;
// Assign the value x + y to z:
let z = x + y;
```
## JavaScript Addition
The **Addition** Operator `(+)` adds numbers:
```js
let x = 5;
let y = 2;
let z = x + y;
```
## JavaScript Multiplication
The Multiplication Operator `(*)` multiplies numbers:
```js
let x = 5;
let y = 2;
let z = x * y;
```
## Types of JavaScript Operators
There are different types of JavaScript operators:

1. Arithmetic Operators
2. Assignment Operators
3. Comparison Operators
4. String Operators
5. Logical Operators
6. Bitwise Operators
7. Ternary Operators
8. Type Operators

### JavaScript Arithmetic Operators
`Arithmetic Operators` are used to perform arithmetic on numbers:
```js
// Define two numbers

```
Explanation:
* Addition (+): Adds two numbers.
* Subtraction (-): Subtracts the second number from the first.
* Multiplication (*): Multiplies two numbers.
* Exponentiation (**): Raises the first number to the power of the second.
* Division (/): Divides the first number by the second.
* Modulus (%): Returns the remainder of the division.
* Increment (++): Increases a variable's value by 1.
* Decrement (--): Decreases a variable's value by 1.

| Operator | Description                        |
|----------|------------------------------------|
| +        | Addition                           |
| -        | Subtraction                        |
| *        | Multiplication                     |
| **       | Exponentiation (ES2016)            |
| /        | Division                           |
| %        | Modulus (Division Remainder)       |
| ++       | Increment                          |
| --       | Decrement                          |

### JavaScript Assignment Operators
Assignment operators assign values to JavaScript variables.

The `Addition Assignment` Operator `(+=)` adds a value to a variable

| Operator | Example    | Same As        |
|----------|------------|----------------|
| =        | x = y      | x = y          |
| +=       | x += y     | x = x + y      |
| -=       | x -= y     | x = x - y      |
| *=       | x *= y     | x = x * y      |
| /=       | x /= y     | x = x / y      |
| %=       | x %= y     | x = x % y      |
| **=      | x **= y    | x = x ** y     |


```js
// Initial values
let x = 10;
let y = 5;

// Simple assignment
x = y;  // Assign the value of y to x
console.log(`x = y: ${x}`);  // Output: x = y: 5

// Add and assign
x += y;  // x = x + y
console.log(`x += y: ${x}`);  // Output: x += y: 10

// Subtract and assign
x -= y;  // x = x - y
console.log(`x -= y: ${x}`);  // Output: x -= y: 5

// Multiply and assign
x *= y;  // x = x * y
console.log(`x *= y: ${x}`);  // Output: x *= y: 25

// Divide and assign
x /= y;  // x = x / y
console.log(`x /= y: ${x}`);  // Output: x /= y: 5

// Modulus and assign
x %= y;  // x = x % y
console.log(`x %= y: ${x}`);  // Output: x %= y: 0

// Exponentiation and assign (ES2016)
x **= y;  // x = x ** y
console.log(`x **= y: ${x}`);  // Output: x **= y: 0

```
explanation:
* `=`: Basic assignment of the value from the right-hand side to the left-hand side.
* `+=`: Adds the right operand to the left operand and assigns the result to the left operand.
* `-=`: Subtracts the right operand from the left operand and assigns the result to the left operand.
* `*=`: Multiplies the left operand by the right operand and assigns the result to the left operand.
* `/=`: Divides the left operand by the right operand and assigns the result to the left operand.
* `%=`: Assigns the remainder when the left operand is divided by the right operand.
* `**=`: Performs exponentiation (raises the left operand to the power of the right operand) and assigns the result to the left operand.

### JavaScript Comparison Operators

| Operator | Description                        |
|----------|------------------------------------|
| `==`       | equal to                           |
| `===`      | equal value and equal type         |
| `!=`       | not equal                          |
| `!==`      | not equal value or not equal type  |
| `>`        | greater than                       |
| `<`        | less than                          |
| `>=`       | greater than or equal to           |
| `<=`       | less than or equal to              |
| `?`        | ternary operator                   |

```js
// Variables for comparison
let a = 10;
let b = 5;

// Using ternary operator to check equality (==)
let equalityCheck = (a == b) ? "a is equal to b" : "a is not equal to b";
console.log(equalityCheck);  // Output: a is not equal to b

// Using ternary operator to check strict equality (===)
let strictEqualityCheck = (a === b) ? "a and b are of equal value and type" : "a and b are not equal in value or type";
console.log(strictEqualityCheck);  // Output: a and b are not equal in value or type

// Using ternary operator to check not equal (!=)
let notEqualCheck = (a != b) ? "a is not equal to b" : "a is equal to b";
console.log(notEqualCheck);  // Output: a is not equal to b

// Using ternary operator to check strict not equal (!==)
let strictNotEqualCheck = (a !== b) ? "a and b are not equal in value or type" : "a and b are equal in value and type";
console.log(strictNotEqualCheck);  // Output: a and b are not equal in value or type

// Using ternary operator to check greater than (>)
let greaterThanCheck = (a > b) ? "a is greater than b" : "a is not greater than b";
console.log(greaterThanCheck);  // Output: a is greater than b

// Using ternary operator to check less than (<)
let lessThanCheck = (a < b) ? "a is less than b" : "a is not less than b";
console.log(lessThanCheck);  // Output: a is not less than b

// Using ternary operator to check greater than or equal to (>=)
let greaterThanOrEqualCheck = (a >= b) ? "a is greater than or equal to b" : "a is less than b";
console.log(greaterThanOrEqualCheck);  // Output: a is greater than or equal to b

// Using ternary operator to check less than or equal to (<=)
let lessThanOrEqualCheck = (a <= b) ? "a is less than or equal to b" : "a is greater than b";
console.log(lessThanOrEqualCheck);  // Output: a is greater than b
```
Explanation:
* `Equality (==)`: Checks if the values of `a` and `b` are the same.
* `Strict equality (===)`: Checks if the values and types of `a` and `b` are the same.
* `Not equal (!=)`: Checks if the values of `a` and `b` are different.
* `Strict not equal (!==)`: Checks if either the values or types of `a` and `b` are different.
* `Greater than (>)`: Checks if `a` is greater than `b`.
* `Less than (<)`: Checks if `a` is less than `b`.
* `Greater than` or `equal to (>=)`: Checks if `a` is greater than or equal to `b`.
* `Less than` or `equal to (<=)`: Checks if `a` is less than or equal to `b`.

### JavaScript Logical Operators
| Operator | Description          |
|---------|----------------------|
| `&& `     | logical and          |
| `||`      | logical or           |
| `!`       | logical not          |

### JavaScript Type Operators
| Operator | Description         |
|---------|---------------------|
| `typeof`    | Returns the type of a variable        |
| `instanceof`      | Returns true if an object is an instance of an object type         |

### JavaScript Bitwise Operators
Bit operators work on 32 bits numbers.

Any numeric operand in the operation is converted into a 32 bit number. The result is converted back to a JavaScript number.

| Operator | Description             | Example      | Same as          | Result | Decimal |
|----------|-------------------------|--------------|------------------|--------|---------|
| `&`        | AND                     | `5 & 1`        | `0101 & 0001`     | 0001   | 1       |
| `|`        | OR                      | `5 | 1`        | `0101 | 0001`      | 0101   | 5       |
| `~`        | NOT                     | `~ 5`          | `~0101`           | 1010   | 10      |
| `^`        | XOR                     | `5 ^ 1`        | `0101 ^ 0001`     | 0100   | 4       |
| `<<`       | left shift              | `5 << 1`       | `0101 << 1`       | 1010   | 10      |
| `>>`       | right shift             | `5 >> 1`       | `0101 >> 1`       | 0010   | 2       |
| `>>>`      | unsigned right shift    | `5 >>> 1`      | `0101 >>> 1`       | 0010   | 2       |
