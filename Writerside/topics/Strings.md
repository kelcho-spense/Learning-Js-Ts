# Strings

### String Data Type in TypeScript

In TypeScript, the **`string`** data type is used to represent textual data. Strings are sequences of characters and can be enclosed in single quotes (`'`), double quotes (`"`), or backticks (`` ` ``). In addition to basic string manipulation, TypeScript supports features like **template strings/literal strings**, **tagged templates**, and **string-to-number conversions**.

---

### 1. **String Data Type**

A `string` in TypeScript can hold any sequence of characters, including letters, numbers, symbols, and spaces. Strings are immutable, meaning once they are created, their content cannot be changed directly.

#### Example:

```typescript
let greeting: string = "Hello, TypeScript!";
let name: string = 'Alice';

console.log(greeting);  // Output: Hello, TypeScript!
console.log(name);      // Output: Alice
```

* **Concatenation**: You can join strings using the `+` operator.

```typescript
let firstName: string = "John";
let lastName: string = "Doe";
let fullName: string = firstName + " " + lastName;
console.log(fullName);  // Output: John Doe
```

* **String length**: You can get the length of a string using `.length`.

```typescript
let phrase: string = "TypeScript is awesome!";
console.log(phrase.length);  // Output: 22
```

---

### 2. **Template Strings/Literal Strings**

Template strings (also known as **template literals**) in TypeScript are a powerful feature that allows for easier string manipulation. They are enclosed in **backticks** (`` ` ``), not single or double quotes, and allow for **string interpolation**, i.e., embedding expressions within strings.

#### Key Features:

* **Multiline strings**: Template literals allow you to write strings across multiple lines without the need for concatenation or escape sequences.
* **Expression interpolation**: You can embed expressions within `${}` syntax.

#### Example:

```typescript
let name: string = "Alice";
let age: number = 30;

// String interpolation (embedding expressions within the string)
let introduction: string = `Hello, my name is ${name} and I am ${age} years old.`;
console.log(introduction); // Output: Hello, my name is Alice and I am 30 years old.
```

#### Multiline string example:

```typescript
let message: string = `This is a multiline
string using template literals.
It allows for easy formatting.`;
console.log(message);
// Output:
// This is a multiline
// string using template literals.
// It allows for easy formatting.
```

---

### 3. **Tagged Templates**

Tagged templates allow you to parse template literals with a function. The **tag function** gets the template literal as an argument, and you can manipulate or process the string and its expressions.

#### Syntax:

```typescript
tagFunction`template literal`
```

The **tag function** takes the literal parts of the string and the embedded expressions as its arguments.

#### Example: Creating a simple tag function:

```typescript
function highlight(strings: TemplateStringsArray, ...values: any[]) {
  let result = "";
  for (let i = 0; i < values.length; i++) {
    result += strings[i] + `<b>${values[i]}</b>`;  // Add bold tags around expressions
  }
  result += strings[values.length];
  return result;
}

let name: string = "Alice";
let age: number = 30;

let message: string = highlight`Hello, my name is ${name} and I am ${age} years old.`;
console.log(message);  // Output: Hello, my name is <b>Alice</b> and I am <b>30</b> years old.
```

In this example:

* The `highlight` function adds `<b>` tags around the dynamic values inside the template string (`${name}` and `${age}`).
* The `strings` array contains the static parts of the template, and `values` holds the dynamic expressions.

---

### 4. **String to Number**

In TypeScript (and JavaScript), you often need to convert a string that represents a number into an actual `number` type. This can be done using several methods, depending on the scenario.

#### 1. **Using `parseInt()`**

The `parseInt()` function converts a string into an integer. It parses the string from left to right and returns the first integer it finds.

```typescript
let str1: string = "42";
let num1: number = parseInt(str1);
console.log(num1);  // Output: 42 (as number)
```

* If the string cannot be converted into a number, `parseInt()` returns `NaN`.

#### Example:

```typescript
let str2: string = "hello";
let num2: number = parseInt(str2);
console.log(num2);  // Output: NaN (Not a Number)
```

#### 2. **Using `parseFloat()`**

The `parseFloat()` function converts a string into a floating-point number. It works similarly to `parseInt()`, but it returns a decimal number.

```typescript
let str3: string = "3.14";
let num3: number = parseFloat(str3);
console.log(num3);  // Output: 3.14
```

#### 3. **Using the Unary Plus (`+`) Operator**

The unary plus operator (`+`) is a shorthand way to convert a string into a number. It tries to convert the value to a number automatically.

```typescript
let str4: string = "100";
let num4: number = +str4;
console.log(num4);  // Output: 100 (as number)
```

#### 4. **Using `Number()` Constructor**

The `Number()` function is a more explicit way to convert a string to a number. It works for both integers and floating-point numbers.

```typescript
let str5: string = "123.45";
let num5: number = Number(str5);
console.log(num5);  // Output: 123.45
```

* If the string is not a valid number, `Number()` returns `NaN`.

#### Example:

```typescript
let str6: string = "Hello World";
let num6: number = Number(str6);
console.log(num6);  // Output: NaN
```

---

### Summary of Key Concepts

| **Concept**          | **Explanation**                                                                         | **Example**                           |
| -------------------- | --------------------------------------------------------------------------------------- | ------------------------------------- |
| **String Data Type** | Represents textual data. Can be enclosed in single quotes, double quotes, or backticks. | `let name: string = "Alice";`         |
| **Template Strings** | Enclosed in backticks. Allows string interpolation and multi-line strings.              | ``let greeting = `Hello, ${name}!`;`` |
| **Tagged Templates** | Allows processing of template literals through a tag function.                          | `highlight\`Hello, \${name}!\`\`      |
| **String to Number** | Converts strings to numbers using `parseInt()`, `parseFloat()`, `+`, or `Number()`.     | `let num = + "123";`                  |

---
