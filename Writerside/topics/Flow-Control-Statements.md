# Control Flow Statements

## JavaScript if, else, and else if
Conditional statements are used to perform different actions based on different conditions.

## Conditional Statements
Very often when you write code, you want to perform different actions for different decisions.

You can use conditional statements in your code to do this.

In JavaScript we have the following conditional statements:

* Use `if` to specify a block of code to be executed, if a specified condition is true
* Use `else` to specify a block of code to be executed, if the same condition is false
* Use `else if` to specify a new condition to test, if the first condition is false
* Use `switch` to specify many alternative blocks of code to be executed

### The if Statement
Use the if statement to specify a block of JavaScript code to be executed if a condition is true.

syntax: 
```js
if (condition) {
  //  block of code to be executed if the condition is true
}
```
example: 
```js
if (hour < 18) {
  greeting = "Good day";
}
```
### The else Statement
Use the `else` statement to specify a block of code to be executed if the condition is false.

syntax:
```js
if (condition) {
  //  block of code to be executed if the condition is true
} else {
  //  block of code to be executed if the condition is false
}
```
example: 
```js
if (hour < 18) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```
### The else if Statement
Use the `else if` statement to specify a new condition if the first condition is false.

Syntax: 
```js
if (condition1) {
  //  block of code to be executed if condition1 is true
} else if (condition2) {
  //  block of code to be executed if the condition1 is false and condition2 is true
} else {
  //  block of code to be executed if the condition1 is false and condition2 is false
}
```

Example:
```js
if (time < 10) {
  greeting = "Good morning";
} else if (time < 20) {
  greeting = "Good day";
} else {
  greeting = "Good evening";
}
```

### JavaScript Switch Statement
The `switch` statement is used to perform different actions based on different conditions.

Syntax:
```js
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

The `getDay()` method returns the weekday as a number between `0` and `6`.

(Sunday=0, Monday=1, Tuesday=2 ..)

This example uses the weekday number to calculate the weekday name:

```js
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
When JavaScript reaches a `break` keyword, it breaks out of the switch block.

This will stop the execution inside the switch block.

It is not necessary to break the last case in a switch block. The block breaks (ends) there anyway.

> _**Note**: If you omit the break statement, the next case will be executed even if the evaluation does not match the case_

### The default Keyword
The `default` keyword specifies the code to run if there is no case match:

The `getDay()` method returns the weekday as a number between 0 and 6.

If today is neither Saturday (6) nor Sunday (0), write a default message:

```js
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
The result of text will be: ```Today is Sunday```

## JavaScript Loops
Loops are handy, if you want to run the same code over and over again, each time with a different value.
JavaScript supports different kinds of loops:

* `for` - loops through a block of code a number of times
* `for/in` - loops through the properties of an object
* `for/of` - loops through the values of an iterable object
* `while` - loops through a block of code while a specified condition is true
* `do/while` - also loops through a block of code while a specified condition is true

### The For Loop
The for statement creates a loop with 3 optional expressions:
syntax: 
```js
for (expression 1; expression 2; expression 3) {
  // code block to be executed
}
```
* `Expression 1` is executed (one time) before the execution of the code block.
* `Expression 2` defines the condition for executing the code block.
* `Expression 3` is executed (every time) after the code block has been executed.

```js
for (let i = 0; i < 5; i++) {
  text += "The number is " + i + "<br>";
}
```
Right-Angled Triangle (ascending order): 
```js
// Define the height of the triangle
let height = 5;

// Using a for loop to print the triangle
for (let row = 1; row <= height; row++) {
    let stars = ''; // Empty string to build each row
    
    // Add '*' to the string for each column in the current row
    for (let column = 1; column <= row; column++) {
        stars += '*';  // Append '*' to the stars string
    }
    
    // Print the row
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
Reversed Right-Angled Triangle (descending order) :
```js
// Define the height of the triangle
let height = 5;

// Using a for loop to print the reversed triangle
for (let row = height; row >= 1; row--) {
    let stars = ''; // Empty string to build each row
    
    // Add '*' to the string for each column in the current row
    for (let column = 1; column <= row; column++) {
        stars += '*';  // Append '*' to the stars string
    }
    
    // Print the row
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


#### Explanation:

* In both examples, we use two `for` loops:

    * The outer loop controls the number of rows.
    * The inner loop controls the number of `*` printed in each row.

For the right-angled triangle:

* The number of `*` increases as the rows go down (from 1 to `height`).

For the reversed right-angled triangle:

* The number of `*` decreases as the rows go down (from `height` to 1).

You can change the `height` variable to create larger or smaller triangles!

### The For In Loop
The JavaScript `for in` statement loops through the properties of `an Object`:

syntax: 
```js
for (key in object) {
  // code block to be executed
}
```
example: 
```js
const person = {fname:"John", lname:"Doe", age:25};

let text = "";
for (let x in person) {
  text += person[x];
}
```

* The `for in` loop iterates over a `person` object
* Each iteration returns a `key (x)`
* The key is used to access the `value` of the key
* The value of the key is `person[x]`

#### For In Over Arrays
The JavaScript `for in` statement can also loop over the properties of an Array:

Syntax:
```js
for (variable in array) {
  code
}
```
Example:
```js
const numbers = [45, 4, 9, 16, 25];

let txt = "";
for (let x in numbers) {
    console.log(numbers[x])
    txt += numbers[x];
}

console.log(txt)
```
### The For Of Loop
The `JavaScript for of` statement loops through the values of an `iterable object`.

It lets you loop over iterable data structures such as `Arrays`, `Strings`, `Maps`, `NodeLists`, and more:

Syntax: 
```js
for (variable of iterable) {
  // code block to be executed
}
```
#### Looping over an Array

```js
const cars = ["BMW", "Volvo", "Mini"];

let text = "";
for (let x of cars) {
    console.log(x)
  text += x;
}
```
#### Looping over a String
```js
let language = "JavaScript";

let text = "";
for (let x of language) {
    console.log(x)
    text += x;
}
```
### forEach
The `forEach` method in JavaScript is used to execute a provided function once for each element in an `array (or array-like object)`. It is commonly used when you need to iterate through an array and perform an operation on each element.

Syntax:
```js
array.forEach(function(element, index, array) {
  // Code to be executed for each element
});
```
* `element`: The current element in the array.
* `index (optional)`: The index of the current element.
* `array (optional)`: The array that `forEach` is being applied to.

* Iterating through an array of numbers
```js
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(number) {
console.log(number * 2); // Multiply each number by 2
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
* Using forEach with an index
```js
let fruits = ["apple", "banana", "cherry"];

fruits.forEach(function(fruit, index) {
    console.log(`${index + 1}: ${fruit}`);
});

```
Output:
```Bash
1: apple
2: banana
3: cherry
```
* Using forEach with arrow functions
```js
let fruits = ["apple", "banana", "cherry"];

fruits.forEach((fruit, index) => {
    console.log(`${index + 1}: ${fruit}`);
});
```
Output:
```bash
1: apple
2: banana
3: cherry
```
* Iterating over an array of objects
```js
let people = [
    { name: "Alice", age: 30 },
    { name: "Bob", age: 25 },
    { name: "Charlie", age: 35 }
];

people.forEach(person => {
    console.log(`${person.name} is ${person.age} years old.`);
});
```
Output:
```Bash
Alice is 30 years old.
Bob is 25 years old.
Charlie is 35 years old.
```
### While loop
The `while` loop loops through a block of code as long as a specified condition is true.

Syntax:
```js
while (condition) {
  // code block to be executed
}
```
To create a right-angled triangle using a while loop in JavaScript, you can build the pattern by printing asterisks (*) row by row, with each row having one more * than the previous one.

Here's an example of how to do it:
```js
// Define the height of the triangle
let height = 5;

// Initialize the starting row
let row = 1;

while (row <= height) {
    let stars = ''; // Empty string to build each row
    
    // Add '*' to the string for each column in the current row
    let column = 1;
    while (column <= row) {
        stars += '*';  // Append '*' to the stars string
        column++;
    }
    
    // Print the row
    console.log(stars);
    
    // Move to the next row
    row++;
}
```
Explanation:
* The `outer while loop` controls the `number of rows (height)`.
* The `inner while loop controls` the number of stars in each row. For `row 1`, it `prints 1 star`, for `row 2`, it `prints 2 stars`, and so on.
* The stars variable is built by concatenating * for each iteration in the inner loop.
* After constructing each row, it is printed to the console using console.log().

For `height = 5`, the output will look like this:

```bash
*
**
***
****
*****
```

To create a `right-angled triangle in reverse` (starting with the largest row of stars and decreasing by one on each line) using a `while loop` in JavaScript, you can do the following:

```js
// Define the height of the triangle
let height = 5;

// Initialize the starting row (same as height)
let row = height;

while (row > 0) {
    let stars = ''; // Empty string to build each row
    
    // Add '*' to the string for each column in the current row
    let column = 1;
    while (column <= row) {
        stars += '*';  // Append '*' to the stars string
        column++;
    }
    
    // Print the row
    console.log(stars);
    
    // Move to the next row (decreasing the row count)
    row--;
}
```
### The Do While Loop
The `do while` loop is a variant of the while loop. This loop will execute the code block once, before checking if the condition is true, then it will repeat the loop as long as the condition is true.

Syntax:
```js
do {
  // code block to be executed
}
while (condition);
```

Example:
The example below uses a `do while` loop. The loop will always be executed at least once, even if the condition is false, because the code block is executed before the condition is tested:
```js
do {
  text += "The number is " + i;
  i++;
}
while (i < 10);
```