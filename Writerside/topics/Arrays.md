# Arrays

An array is a special variable, which can hold more than one value:
```js
const cars = ["Saab", "Volvo", "BMW"];
```

## Why Use Arrays?

If you have a list of items (a list of car names, for example), storing the cars in single variables could look like this:
```js
let car1 = "Saab";
let car2 = "Volvo";
let car3 = "BMW";
```
However, what if you want to loop through the cars and find a specific one? And what if you had not 3 cars, but 300?

The solution is an array!

An array can hold many values under a single name, and you can access the values by referring to an index number.

## Creating an Array
Syntax:
```js
const array_name = [item1, item2, ...];   
```   
> _It is a common practice to declare arrays with the const keyword._

```js
const cars = ["Saab", "Volvo", "BMW"];
```
or 
```js
const cars = [
  "Saab",
  "Volvo",
  "BMW"
];
```
### Using the JavaScript Keyword `new`
```js
const cars = new Array("Saab", "Volvo", "BMW");
```
> The two examples above do exactly the same. There is no need to use `new Array()`. For simplicity, readability and execution speed, use the array literal method.

## Accessing First Array Elements
You access an array element by referring to the `index number`:
```js
const cars = ["Saab", "Volvo", "BMW"];
let car = cars[0];
```
> Note: Array indexes **start with 0**. `[0]` is the `first element`. `[1]` is the `second element`.

## Accessing the Last Array Element
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
let fruit = fruits[fruits.length - 1];
```

## Changing an Array Element
This statement changes the value of the first element in cars:
```js
cars[0] = "Saab"
```
## Looping Array Elements
With JavaScript, the full array can be accessed by referring to the array name:
- ### `Array.forEach()`
```js
cars.forEach((item, index)=> {
    console.log(`the index: ${index} and the value : ${item}`)
})
```
- ### `for`
```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];
let fLen = fruits.length;

let text = "<ul>";
for (let i = 0; i < fLen; i++) {
  text += "<li>" + fruits[i] + "</li>";
}
text += "</ul>";
```

## Arrays are Objects
> * Arrays are a special type of objects. The `typeof` operator in JavaScript returns `"object" for arrays`.
> * But, JavaScript arrays are best described as arrays.
> * Arrays use numbers to access its "elements". In this example, `person[0]` returns John:

```js
const cars = ["Saab", "Volvo", "BMW"];

console.log(typeof cars) // "object"  
```
## Array Methods
- `push()` : add an element at the end of an Array
```js
let a = [10, 20, 30, 40, 50];
a.push(60);
a.push(70, 80, 90);
console.log(a);
```
Output : 
```js
[ 10, 20, 30, 40, 50,  60, 70, 80, 90 ]
```
- `unshift()` : is used to add elements to the front of an Array.
```js
let a = [20, 30, 40];
a.unshift(10, 20);
console.log(a);
```
Output
```js
[ 10, 20, 20, 30, 40 ]
```
- `pop()` : is used to remove elements from the end of an array.  
```js
let a = [20, 30, 40, 50];
a.pop();
console.log(a);
```
- `shift()` : is used to remove elements from the beginning of an array
```js
let a = [20, 30, 40, 50];
a.shift();
console.log(a);
```
Output: 
```js
[ 30, 40, 50 ]
```
- The `splice()` : is used to Insert and Remove elements in between the Array.
```js
let a = [20, 30, 40, 50];
a.splice(1, 3);
a.splice(1, 0, 3, 4, 5);
console.log(a);
```
Output:
```js
[ 20, 3, 4, 5 ]
```
* The first `a.splice(1, 3)` removes 3 elements `(30, 40, 50)` starting at index 1. The array becomes `[20]`.
* The second `a.splice(1, 0, 3, 4, 5)` inserts `3, 4,` and `5` at index 1 without removing anything. The array becomes `[20, 3, 4, 5]`.

- The `slice()` : returns a new array containing a portion of the original array, based on `the start` and `end index` provided as arguments
```js
const a = [1, 2, 3, 4, 5];
const res = a.slice(1, 4);
console.log(res); 
console.log(a)
```
output:
```js
[ 2, 3, 4 ]
[ 1, 2, 3, 4, 5 ]
```
* The `slice()` method creates a new array by extracting elements from `index 1 to 3 (exclusive of 4)` from the original array.
* The original array remains unchanged, and the result is `[2, 3, 4]`.

- `map()` : creates an array by `calling a specific function` on each element present in the parent array. It is a non-mutating method.
```js
let a = [4, 9, 16, 25];
let sub = a.map(geeks);

function geeks() {
    return a.map(Math.sqrt);
}
console.log(sub);
```
Output: 
```js
[ [ 2, 3, 4, 5 ], [ 2, 3, 4, 5 ], [ 2, 3, 4, 5 ], [ 2, 3, 4, 5 ] ]
```
* The code defines a geeks function, but instead of operating on the individual array ‘a’ elements, it applies `Math.sqrt()` to the entire a array, resulting in a `nested array of square roots`.
* The output will be an array of the same length as a, but each element will be the result of applying `arr.map(Math.sqrt)`.

- The `reduce()` method is used to reduce the array to a single value and executes a provided `function for each value of the array (from left to right)` and the return value of the function is stored in an accumulator.
```js
let a = [88, 50, 25, 10];
let sub = a.reduce(geeks);

function geeks(tot, num) {
    return tot - num;
}
console.log(sub);
```
Output: `3`

* The `reduce()` method iterates over the array ‘a’ and applies the geeks function, which subtracts each element (num) from the running total (tot).
* For the array `[88, 50, 25, 10]`, the calculation proceeds as: `88 – 50 – 25 – 10`.

- The `reverse()` method is used to reverse the order of elements in an array. It modifies the array in place and returns a reference to the same array with the reversed order.

```js
let a = [1, 2, 3, 4, 5];
console.log(a);
a.reverse();
console.log(a);
```
Output: 
```js
[1,2,3,4,5]
[ 5, 4, 3, 2, 1 ]
```