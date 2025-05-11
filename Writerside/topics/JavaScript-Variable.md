# JavaScript Variable

JavaScript variables are storage for data, where programs can store value. Basically, It’s an area of memory where JavaScript stores the data.

We usually assign a name to the memory. The programs can then use the variable name to identify the memory location. It makes the coding easier.

![image_2.png](image_2.png)
```js
 
let num;
let messsage;
let isValid;
 
num=5
message="Hello"
isValid=true;
```
In **JavaScript**, a variable can store just about anything like `numbers`, `strings`, `objects`, `arrays`, etc. There are no restrictions on that. This is different from other languages like `C#` & `Java`, where a variable that stores numbers can only `store numbers and nothing else`.

## Declaring the variable
We need to create the variables before using them. In JavaScript, we call it declaring the variable. There are three keywords using which we can declare a variable.
* var
* let
* const

### **Note**
* The `var` keyword was used in all JavaScript code from `1995` to `2015`.
* The `let` and const keywords were added to JavaScript in `2015`.
* The `var` keyword should only be used in code written for `older browsers`.

Example using let:
```js
let x = 5;
let y = 6;
let z = x + y;
```
Example using const: 
```js
const x = 5;
const y = 6;
const z = x + y;
```
Example using var:
```js
var x = 5;
var y = 6;
var z = x + y;
```

### JavaScript Identifiers
All JavaScript `variables` must be `identified` with `unique names`.

These unique names are called `identifiers`.

Identifiers can be short names (like x and y) or more descriptive names (age, sum, totalVolume).

The general rules for constructing names for variables (unique identifiers) are:

1. Names can contain letters, digits, underscores, and dollar signs.
2. Names must begin with a letter.
3. Names can also begin with $ and _ (but we will not use it in this tutorial).
4. Names are case sensitive (y and Y are different variables).
5. Reserved words (like JavaScript keywords) cannot be used as names.

## Var vs Let
The main difference between var and let in JavaScript lies in their scope and behavior:
* Scope:
  * **var**: Has function scope, meaning it is `accessible throughout the entire function` where it is declared (even if declared inside a block like an if statement).
  * **let**: Has block scope, meaning it is `only accessible within the block (like inside {})` where it is declared.
```js
function testVarLet() {
    if (true) {
        var varVar = "I am a var";
        let letVar = "I am a let";
    }
    
    console.log(varVar); // Works fine, 'var' has function scope
    console.log(letVar); // Error: letVar is not defined, because 'let' has block scope
}

testVarLet();
```
* Hoisting:
  * **var**: Variables declared with var `are hoisted to the top of their scope, but their initialization is not`. This can lead to unexpected behavior if accessed before being assigned.
  * **let**: Variables declared with let are `also hoisted, but they remain in a "temporal dead zone" until the declaration is encountered`, which prevents accidental access before the declaration.
```js
function hoistingExample() {
    console.log(varVar); // Undefined due to hoisting
    // console.log(letVar); // Error: Cannot access 'letVar' before initialization

    var varVar = "I am a var";
    let letVar = "I am a let";
}

hoistingExample();
```
* Re-declaration:
  * **var**: You can `re-declare the same variable multiple times` within the same scope without any errors.
  * **let**: You `cannot re-declare a variable in the same scope`.
```js
function redeclarationExample() {
    var x = 10;
    var x = 20; // No error, var allows re-declaration

    let y = 10;
    // let y = 20; // Error: Identifier 'y' has already been declared
}

redeclarationExample();
```