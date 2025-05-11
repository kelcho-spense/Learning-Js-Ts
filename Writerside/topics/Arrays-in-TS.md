# Arrays in TS

An array in TypeScript is a special variable that can hold more than one value. Arrays in TypeScript allow you to work with ordered collections of items of any type.

```ts
const cars: string[] = ["Saab", "Volvo", "BMW"];
```

---

### **Why Use Arrays?**

If you have a list of items (such as car names), you could store them in individual variables like this:

```ts
let car1: string = "Saab";
let car2: string = "Volvo";
let car3: string = "BMW";
```

However, if you have more items or if the number of items is dynamic (e.g., 300 cars), managing them in individual variables becomes cumbersome.

The solution is an array! An array can hold many values under a single name, and you can access the values by referring to an index number.

---

### **Creating an Array**

The general syntax for creating an array is:

```ts
const arrayName: type[] = [item1, item2, ...];   
```

#### Example:

```ts
const cars: string[] = ["Saab", "Volvo", "BMW"];
```

Alternatively, you can use the `Array` constructor:

```ts
const cars: Array<string> = new Array("Saab", "Volvo", "BMW");
```

> **Note**: It is a common practice to declare arrays with the `const` keyword, as arrays are mutable by default in TypeScript.

---

### **Accessing Array Elements**

You access an array element by referring to the **index number** (starting from 0):

```ts
const cars: string[] = ["Saab", "Volvo", "BMW"];
let car: string = cars[0];  // Access the first element
console.log(car);  // Output: Saab
```

#### **Accessing the Last Array Element:**

```ts
const fruits: string[] = ["Banana", "Orange", "Apple", "Mango"];
let fruit: string = fruits[fruits.length - 1];
console.log(fruit);  // Output: Mango
```

---

### **Changing an Array Element**

You can change an array element by referring to its index:

```ts
const cars: string[] = ["Saab", "Volvo", "BMW"];
cars[0] = "Tesla";  // Changes the first element
console.log(cars);  // Output: ["Tesla", "Volvo", "BMW"]
```

---

### **Looping Through Array Elements**

You can loop through arrays using various methods.

#### **Using `forEach()`**

```ts
const cars: string[] = ["Saab", "Volvo", "BMW"];
cars.forEach((item, index) => {
    console.log(`The index: ${index} and the value: ${item}`);
});
```

#### **Using `for` loop**

```ts
const fruits: string[] = ["Banana", "Orange", "Apple", "Mango"];
let text: string = "<ul>";
for (let i = 0; i < fruits.length; i++) {
    text += "<li>" + fruits[i] + "</li>";
}
text += "</ul>";
console.log(text);  // Output: HTML list with fruit names
```

---

### **Arrays are Objects**

Arrays in TypeScript are a special type of object. The `typeof` operator will return `"object"` for arrays.

```ts
const cars: string[] = ["Saab", "Volvo", "BMW"];
console.log(typeof cars);  // Output: "object"
```

---

### **Array Methods**

TypeScript arrays come with several built-in methods for manipulating array elements:

#### **`push()`**: Add an element to the end of an array

```ts
let a: number[] = [10, 20, 30, 40, 50];
a.push(60);
a.push(70, 80, 90);
console.log(a);  // Output: [10, 20, 30, 40, 50, 60, 70, 80, 90]
```

#### **`unshift()`**: Add elements to the front of an array

```ts
let a: number[] = [20, 30, 40];
a.unshift(10, 20);
console.log(a);  // Output: [10, 20, 20, 30, 40]
```

#### **`pop()`**: Remove elements from the end of an array

```ts
let a: number[] = [20, 30, 40, 50];
a.pop();
console.log(a);  // Output: [20, 30, 40]
```

#### **`shift()`**: Remove elements from the beginning of an array

```ts
let a: number[] = [20, 30, 40, 50];
a.shift();
console.log(a);  // Output: [30, 40, 50]
```

#### **`splice()`**: Insert and remove elements from an array

```ts
let a: number[] = [20, 30, 40, 50];
a.splice(1, 3);  // Remove 3 elements starting at index 1
a.splice(1, 0, 3, 4, 5);  // Insert elements 3, 4, and 5 at index 1
console.log(a);  // Output: [20, 3, 4, 5]
```

#### **`slice()`**: Extract a portion of an array and return it as a new array

```ts
const a: number[] = [1, 2, 3, 4, 5];
const res: number[] = a.slice(1, 4);  // Extract from index 1 to 3
console.log(res);  // Output: [2, 3, 4]
console.log(a);    // Output: [1, 2, 3, 4, 5] (original array remains unchanged)
```

#### **`map()`**: Create a new array by applying a function to each element

```ts
let a: number[] = [4, 9, 16, 25];
let sub: number[] = a.map(Math.sqrt);
console.log(sub);  // Output: [2, 3, 4, 5]
```

#### **`reduce()`**: Reduce the array to a single value

```ts
let a: number[] = [88, 50, 25, 10];
let sub: number = a.reduce((tot, num) => tot - num);
console.log(sub);  // Output: 3
```

#### **`reverse()`**: Reverse the order of elements in an array

```ts
let a: number[] = [1, 2, 3, 4, 5];
console.log(a);  // Output: [1, 2, 3, 4, 5]
a.reverse();
console.log(a);  // Output: [5, 4, 3, 2, 1]
```

---

### **Arrays with TypeScript Features**

* **Typed Arrays**: TypeScript allows you to strongly type arrays to ensure that all elements are of the same type.

```ts
const cars: string[] = ["Saab", "Volvo", "BMW"];
const numbers: number[] = [1, 2, 3, 4, 5];
```

* **Array with Mixed Types**: If you need an array with elements of different types, you can use a tuple.

```ts
const carDetails: [string, number] = ["Saab", 2021];
```

* **Readonly Arrays**: If you want to ensure that an array cannot be modified, you can use the `ReadonlyArray<T>` type.

```ts
const readonlyCars: ReadonlyArray<string> = ["Saab", "Volvo", "BMW"];
// readonlyCars.push("Audi");  // Error: Property 'push' does not exist on type 'readonly string[]'.
```

---

### **Conclusion**

Arrays in TypeScript work similarly to JavaScript arrays, but with strong typing. TypeScript ensures that arrays are more predictable and helps to catch errors at compile-time. You can use array methods such as `push()`, `pop()`, `shift()`, `unshift()`, `map()`, `filter()`, and `reduce()`, among others, while taking advantage of TypeScript's type checking to avoid runtime issues.

This comprehensive guide covers all the essential array operations and demonstrates how they are strongly typed in TypeScript.
