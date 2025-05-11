# Functions

JavaScript functions are defined with the `function` keyword.

```js
function functionName(parameters) {
  // code to be executed
}
```
example: 
```js
function myFunction(a, b) {
  return a * b;
}
```
### Function Hoisting
* Hoisting is JavaScript's default behavior of moving `declarations` to the top of the current scope.
* Hoisting applies to variable declarations and to function declarations.
* Because of this, JavaScript functions can be called before they are declared:
```js
myFunction(5);

function myFunction(y) {
  return y * y;
}
```

### Function Parameters and Arguments
* Function `parameters` are the names listed in the function definition.
* Function `arguments` are the real values passed to (and received by) the function.
Syntax: 
```js
function functionName(parameter1, parameter2, parameter3) {
  // code to be executed
}
```
### Default Parameter Values
```js
function myFunction(x, y = 10) {
  return x + y;
}
myFunction(5);
```

## Types Function 

### Arrow Functions

Arrow functions allows a short syntax for writing function expressions.

You don't need the `function` keyword, the `return` keyword, and the `curly brackets`.
```js
// ES5
var x = function(x, y) {
  return x * y;
}

// ES6
const x = (x, y) => x * y;
```

### Immediately-invoked Function Expressions (IIFE)
Function expressions can be made "self-invoking".

A self-invoking expression is invoked (started) automatically, without being called.

Syntax:
```js
 
(function() {
    // statements
})()
```
Example:
```js
(function () {
  let x = "Hello!!";  // I will invoke myself
})();
```