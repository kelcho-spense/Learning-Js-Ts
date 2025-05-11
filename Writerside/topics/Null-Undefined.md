# Null &amp; Undefined

### **Null and Undefined in TypeScript**

In TypeScript, `null` and `undefined` are both primitive values, but they represent different concepts. Understanding the difference between them is crucial to writing robust TypeScript code.

---

### **1. `null`**

* **Definition:** `null` represents an intentional absence of any object value. It is explicitly assigned to a variable to indicate that the variable should not hold any valid data.
* **Usage:** It is typically used to indicate that a variable will eventually hold an object, but at the moment it is explicitly set to no value.

#### Example of `null`:

```typescript
let person: { name: string, age: number } | null = null;  // person can either hold an object or be null

if (person === null) {
    console.log("No person found.");
} else {
    console.log(`Name: ${person.name}, Age: ${person.age}`);
}
// Output: No person found.
```

In this example, the `person` variable is explicitly set to `null`, indicating that there is no person data available.

---

### **2. `undefined`**

* **Definition:** `undefined` represents an uninitialized or absent value. It is the default value for uninitialized variables, function parameters, or object properties.
* **Usage:** It is used by JavaScript/TypeScript when a variable is declared but not assigned a value, or when a function does not return a value.

#### Example of `undefined`:

```typescript
let name: string;

console.log(name);  // Output: undefined
```

In the above example, the variable `name` is declared but not assigned any value, so it holds the value `undefined`.

---

### **3. Strict Null Checks in TypeScript**

TypeScript's **Strict Null Checks** is a setting that provides stricter type checking regarding `null` and `undefined`. When **strict null checks** are enabled (in `tsconfig.json`), the types `null` and `undefined` are not assignable to other types (except `null` and `undefined` themselves, or `any`).

#### Why Strict Null Checks?

In the default (non-strict) mode, `null` and `undefined` are treated as valid values for any type, which can lead to potential bugs if you unintentionally access properties or methods on `null` or `undefined` values.

For example:

```typescript
let name: string;
name = null;  // Allowed by default
name = undefined;  // Allowed by default
```

With **strict null checks** enabled, TypeScript will enforce that `null` and `undefined` are treated separately from other types:

#### Enabling Strict Null Checks:

In your `tsconfig.json`:

```json
{
  "compilerOptions": {
    "strictNullChecks": true
  }
}
```

With **strict null checks** enabled:

```typescript
let name: string;

name = null;        // Error: Type 'null' is not assignable to type 'string'.
name = undefined;   // Error: Type 'undefined' is not assignable to type 'string'.
```

Now, `null` and `undefined` are not implicitly assignable to variables of type `string`. This helps in catching errors early in the development process and avoids unexpected `null` or `undefined` values causing runtime errors.

---

### **4. Null vs Undefined**

Both `null` and `undefined` represent absence or lack of value, but they are used in different contexts.

| **Aspect**              | **`null`**                                      | **`undefined`**                                             |
| ----------------------- | ----------------------------------------------- | ----------------------------------------------------------- |
| **Meaning**             | Explicit absence of a value (empty or unknown). | A variable has been declared but not assigned a value.      |
| **Type**                | `null` is its own type.                         | `undefined` is also its own type.                           |
| **Assigned by default** | **No**, it must be explicitly assigned.         | **Yes**, automatically assigned to uninitialized variables. |
| **Usage**               | Used intentionally to represent no value.       | Used when variables are declared but not initialized.       |
| **Example**             | `let person = null;`                            | `let person; console.log(person);` (outputs `undefined`)    |

#### Example of `null` and `undefined`:

```typescript
let item1: string | null = null;      // null represents no value
let item2: string | undefined;        // undefined, uninitialized

console.log(item1);  // Output: null
console.log(item2);  // Output: undefined
```

In this example:

* `item1` is explicitly set to `null`, indicating that no value is assigned.
* `item2` is declared but not assigned any value, so it automatically holds `undefined`.

#### Null vs Undefined in Functions:

```typescript
function greet(name: string | null): string {
  if (name === null) {
    return "Hello, Guest!";
  }
  return `Hello, ${name}!`;
}

console.log(greet(null));   // Output: Hello, Guest!
console.log(greet(undefined));   // Output: Error in strict mode, `undefined` is not assignable to `string | null`
```

In the above code, the function accepts `name` which can either be a string or `null`. However, passing `undefined` is not allowed in **strict mode** because `undefined` is not a valid value for the `string | null` type.

---

### **5. Difference Between `null` and `undefined` in TypeScript**

| **Aspect**           | **`null`**                                                      | **`undefined`**                                                            |
| -------------------- | --------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Intent**           | Represents intentional absence of a value.                      | Represents uninitialized or absent value.                                  |
| **Assigned Value**   | Explicitly assigned `null` to a variable.                       | Automatically assigned by JavaScript to uninitialized variables.           |
| **Default Behavior** | Never automatically assigned, must be set manually.             | Automatically assigned to variables that are declared but not initialized. |
| **Type**             | `null` is a primitive type.                                     | `undefined` is also a primitive type.                                      |
| **Equality**         | `null == undefined` is true, but `null === undefined` is false. | `undefined` is a more general concept.                                     |

---

### **Conclusion:**

* **`null`** represents an intentional absence of any value and is explicitly assigned.
* **`undefined`** represents an uninitialized value or variable.
* **Strict Null Checks** in TypeScript enforce better handling of `null` and `undefined` by preventing accidental assignment of these values to non-nullable types.
* Enabling **strict null checks** increases code safety, making sure that `null` and `undefined` are not implicitly assigned to variables of other types, which prevents runtime errors due to null dereferencing.

By understanding the differences between `null` and `undefined` and leveraging TypeScript's `strictNullChecks`, developers can write cleaner and more robust code that is less prone to errors.
