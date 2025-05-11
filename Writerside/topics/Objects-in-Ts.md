# Objects in Ts

### 1. **Real Life Objects**
![image_3.png](image_3.png)

Objects in TypeScript are key-value pairs that represent real-world entities. For example, a "car" object might have properties like `make`, `model`, and `year`. These objects can represent almost anything in real life.

**Example**:

```typescript
let car = {
  make: "Toyota",
  model: "Corolla",
  year: 2021
};
```

In this example, `car` is a real-life object with properties like `make`, `model`, and `year`. TypeScript provides type safety for objects by allowing us to specify types for properties.

---

### 2. **Creating a JavaScript Object**

In TypeScript, creating objects is similar to JavaScript, but we can also add type annotations for stricter type-checking.

**Example**:

```typescript
// Object with inferred types
let person = {
  name: "John",
  age: 30,
  greet() {
    console.log("Hello " + this.name);
  }
};

// Object with explicit types
let employee: { name: string; age: number; jobTitle: string } = {
  name: "Jane",
  age: 35,
  jobTitle: "Developer"
};
```

Here, the `employee` object is explicitly typed using the `{ name: string; age: number; jobTitle: string }` syntax, which ensures that all properties must match the specified types.

---

### 3. **Object Properties**

Object properties can be accessed in two ways: dot notation or bracket notation. TypeScript will infer types based on the values provided unless explicitly declared.

**Example**:

```typescript
let car = {
  make: "Toyota",
  model: "Corolla",
  year: 2021
};

console.log(car.make);  // Accessing property using dot notation
console.log(car["model"]);  // Accessing property using bracket notation
```

You can also create an object with **optional properties** or **read-only properties**.

**Optional Property Example**:

```typescript
let person: { name: string; age: number; jobTitle?: string } = {
  name: "Jane",
  age: 35
};
```

In this example, the `jobTitle` is optional.

---

### 4. **Accessing Object Properties**

In TypeScript, properties can be accessed in the usual ways: dot notation or bracket notation. TypeScript ensures type safety while accessing object properties.

**Example**:

```typescript
let user = {
  name: "Alice",
  age: 28
};

let userName: string = user.name;  // Access property using dot notation
let userAge: number = user["age"];  // Access property using bracket notation
```

In this case, `userName` will be inferred as `string`, and `userAge` will be inferred as `number`.

---

### 5. **JavaScript Object Methods**

Objects in TypeScript can have methods (functions) as well. Methods can access object properties using `this`.

**Example**:

```typescript
let calculator = {
  num1: 5,
  num2: 10,
  add() {
    return this.num1 + this.num2;
  },
  multiply() {
    return this.num1 * this.num2;
  }
};

console.log(calculator.add());       // Output: 15
console.log(calculator.multiply());  // Output: 50
```

In this case, the methods `add` and `multiply` are defined in the `calculator` object. TypeScript automatically infers the types of `num1` and `num2` based on the object properties.

---