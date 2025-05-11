# Control Flow Statements in TS


## TypeScript if, else, and else if

Conditional statements are used to perform different actions based on different conditions.

## Conditional Statements

Very often when you write code, you want to perform different actions for different decisions.

You can use conditional statements in your code to do this.

In TypeScript we have the following conditional statements:

* Use `if` to specify a block of code to be executed, if a specified condition is true
* Use `else` to specify a block of code to be executed, if the same condition is false
* Use `else if` to specify a new condition to test, if the first condition is false
* Use `switch` to specify many alternative blocks of code to be executed

### The if Statement

Use the if statement to specify a block of TypeScript code to be executed if a condition is true.

syntax:

```ts
if (condition) {
  //  block of code to be executed if the condition is true
}
```

example:

```ts
let greeting: string;
let hour: number = 15;
if (hour < 18) {
  greeting = "Good day";
}
```

### The else Statement

Use the `else` statement to specify a block of code to be executed if the condition is false.

syntax:

```ts
if (condition) {
  //  block of code to be executed if the condition is true
} else {
  //  block of code to be executed if the condition is false
}
```

example:

```ts
let greeting: string;
let hour: number = 15;
if (hour < 18) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

### The else if Statement

Use the `else if` statement to specify a new condition if the first condition is false.

Syntax:

```ts
if (condition1) {
  //  block of code to be executed if condition1 is true
} else if (condition2) {
  //  block of code to be executed if condition1 is false and condition2 is true
} else {
  //  block of code to be executed if condition1 is false and condition2 is false
}
```

Example:

```ts
let greeting: string;
let time: number = 20;
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

### TypeScript Switch Statement

The `switch` statement is used to perform different actions based on different conditions.

Syntax:

```ts
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```

This is how it works:

* The switch expression is evaluated once.
* The value of the expression is compared with the values of each case.
* If there is a match, the associated block of code is executed.
* If there is no match, the default code block is executed.

The `getDay()` method returns the weekday as a number between `0` and `6` (Sunday=0, Monday=1, Tuesday=2...).

```ts
let day: string;
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
     day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case 6:
    day = "Saturday";
}
```

### The break Keyword

When TypeScript reaches a `break` keyword, it breaks out of the switch block.

This will stop the execution inside the switch block.

It is not necessary to break the last case in a switch block. The block breaks (ends) there anyway.

> ***Note**: If you omit the break statement, the next case will be executed even if the evaluation does not match the case.*

### The default Keyword

The `default` keyword specifies the code to run if there is no case match:

The `getDay()` method returns the weekday as a number between 0 and 6.

```ts
let text: string;
switch (new Date().getDay()) {
  case 6:
    text = "Today is Saturday";
    break;
  case 0:
    text = "Today is Sunday";
    break;
  default:
    text = "Looking forward to the Weekend";
}
```

The result of text will be: `"Today is Sunday"`

## TypeScript Loops

Loops are handy, if you want to run the same code over and over again, each time with a different value.
TypeScript supports different kinds of loops:

* `for` - loops through a block of code a number of times
* `for/in` - loops through the properties of an object
* `for/of` - loops through the values of an iterable object
* `while` - loops through a block of code while a specified condition is true
* `do/while` - also loops through a block of code while a specified condition is true

### The For Loop

The `for` statement creates a loop with 3 optional expressions:

Syntax:

```ts
for (expression1; expression2; expression3) {
  // code block to be executed
}
```

* `Expression 1` is executed (one time) before the execution of the code block.
* `Expression 2` defines the condition for executing the code block.
* `Expression 3` is executed (every time) after the code block has been executed.

```ts
let text: string = "";
for (let i = 0; i < 5; i++) {
  text += "The number is " + i + "<br>";
}
```

Right-Angled Triangle (ascending order):

```ts
let height: number = 5;

for (let row = 1; row <= height; row++) {
    let stars = '';
    for (let column = 1; column <= row; column++) {
        stars += '*';
    }
    console.log(stars);
}
```

Output for `height = 5`:

```bash
*
**
***
****
*****
```

Reversed Right-Angled Triangle (descending order):

```ts
let height: number = 5;

for (let row = height; row >= 1; row--) {
    let stars = '';
    for (let column = 1; column <= row; column++) {
        stars += '*';
    }
    console.log(stars);
}
```

Output for `height = 5`:

```bash
*****
****
***
**
*
```

### The For In Loop

The TypeScript `for in` statement loops through the properties of an Object:

Syntax:

```ts
for (key in object) {
  // code block to be executed
}
```

Example:

```ts
const person = { fname: "John", lname: "Doe", age: 25 };

let text: string = "";
for (let x in person) {
  text += person[x];
}
```

### For In Over Arrays

The TypeScript `for in` statement can also loop over the properties of an Array:

Syntax:

```ts
for (variable in array) {
  // code block to be executed
}
```

Example:

```ts
const numbers: number[] = [45, 4, 9, 16, 25];

let txt: string = "";
for (let x in numbers) {
  console.log(numbers[x]);
  txt += numbers[x];
}
```

### The For Of Loop

The TypeScript `for of` statement loops through the values of an iterable object.

It lets you loop over iterable data structures such as `Arrays`, `Strings`, `Maps`, `NodeLists`, and more:

Syntax:

```ts
for (variable of iterable) {
  // code block to be executed
}
```

Example:

```ts
const cars: string[] = ["BMW", "Volvo", "Mini"];

let text: string = "";
for (let x of cars) {
    console.log(x);
    text += x;
}
```

### forEach

The `forEach` method in TypeScript is used to execute a provided function once for each element in an `array` (or array-like object). It is commonly used when you need to iterate through an array and perform an operation on each element.

Syntax:

```ts
array.forEach(function(element, index, array) {
  // Code to be executed for each element
});
```

Example:

```ts
let numbers: number[] = [1, 2, 3, 4, 5];

numbers.forEach(function(number) {
  console.log(number * 2);
});
```

Output:

```bash
2
4
6
8
10
```

### While loop

The `while` loop loops through a block of code as long as a specified condition is true.

Syntax:

```ts
while (condition) {
  // code block to be executed
}
```

Example:

```ts
let height: number = 5;
let row: number = 1;

while (row <= height) {
    let stars: string = '';
    let column: number = 1;
    while (column <= row) {
        stars += '*';
        column++;
    }
    console.log(stars);
    row++;
}
```

Output for `height = 5`:

```bash
*
**
***
****
*****
```

### The Do While Loop

The `do while` loop is a variant of the `while` loop. This loop will execute the code block once, before checking if the condition is true, then it will repeat the loop as long as the condition is true.

Syntax:

```ts
do {
  // code block to be executed
}
while (condition);
```

Example:

```ts
let i: number = 0;
let text: string = "";
do {
  text += "The number is " + i;
  i++;
} while (i < 10);
```

---
