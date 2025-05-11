# Scope, Scope Chain, Lexical Scope &amp; Closure

In JavaScript, understanding **scope**, **scope chain**, **lexical scope**, and **closure** is fundamental to writing efficient and bug-free code. Let’s break down these concepts one by one, with detailed explanations and examples.

### 1. **Scope**

**Scope** refers to the context or environment in which variables and functions are accessible. It defines the visibility and lifetime of variables and functions in different parts of your code.

There are primarily two types of scopes in JavaScript:

* **Global Scope**: Variables declared outside any function are in the global scope. They can be accessed from anywhere in the code.

* **Local Scope**: Variables declared inside a function are in the local scope of that function. They can only be accessed within that function.

#### Example:

```javascript
let globalVar = "I am global"; // Global scope

function exampleFunction() {
    let localVar = "I am local"; // Local scope
    console.log(globalVar); // Can access global variable
    console.log(localVar); // Can access local variable
}

exampleFunction();

console.log(globalVar); // Can access global variable
console.log(localVar); // Error! localVar is not defined
```

#### Explanation:

* `globalVar` is defined in the **global scope** and can be accessed both inside and outside the function.
* `localVar` is defined inside the function `exampleFunction()` and can only be accessed within that function. Attempting to access `localVar` outside the function results in an error.

### 2. **Scope Chain**

The **scope chain** is the order in which the JavaScript engine looks for a variable. When you try to access a variable, JavaScript looks for it in the **local scope** first, then moves outward to the **parent scope** (if any), and finally looks in the **global scope**. The scope chain helps JavaScript determine the value of a variable.

#### Example:

```javascript
let globalVar = "I am global"; // Global scope

function outerFunction() {
    let outerVar = "I am in outer function"; // Local scope of outerFunction

    function innerFunction() {
        let innerVar = "I am in inner function"; // Local scope of innerFunction
        console.log(innerVar); // Accessing local variable inside innerFunction
        console.log(outerVar); // Accessing variable from outerFunction scope
        console.log(globalVar); // Accessing global variable
    }

    innerFunction();
}

outerFunction();
```

#### Explanation:

* The **scope chain** works as follows:

    1. When `innerFunction()` is called, it first checks for `innerVar` in its own scope (the local scope of `innerFunction`).
    2. If `innerVar` isn’t found, it checks the **outer function's scope** (`outerFunction()`), and then the **global scope** if necessary.
    3. The scope chain enables `innerFunction()` to access `outerVar` from its parent scope (`outerFunction`) and `globalVar` from the global scope.

### 3. **Lexical Scope**

**Lexical scope** (also called **static scope**) means that the **scope of a variable is determined by where the variable is declared in the code** (at the time of writing, not at runtime). In other words, functions are able to access variables from their outer (parent) scopes based on where they were defined, not where they are executed.

#### Example:

```javascript
function outer() {
    let outerVar = "I am in outer";

    function inner() {
        console.log(outerVar); // Accesses outerVar due to lexical scoping
    }

    inner();
}

outer();
```

#### Explanation:

* `inner()` has access to `outerVar` because of **lexical scoping**. It was **lexically** defined within `outer()`, so it can access `outerVar`, even though `inner()` is invoked within the function `outer()`.

In JavaScript, **lexical scoping** ensures that functions always remember where they were created, not where they are invoked.

### 4. **Closure**

A **closure** is a function that retains access to its lexical scope, even when the function is executed outside of that scope. In simpler terms, a closure is a function that “remembers” the environment in which it was created.

A closure happens when:

* A function is defined inside another function.
* The inner function references variables from the outer function.

#### Example:

```javascript
function outer() {
    let counter = 0; // Local variable in outer

    return function inner() {
        counter++; // The inner function has access to counter
        console.log(counter);
    };
}

const increment = outer(); // `increment` is now a closure
increment(); // Logs 1
increment(); // Logs 2
increment(); // Logs 3
```

#### Explanation:

* `inner()` is a closure because it retains access to the variable `counter` from its **lexical scope** (the `outer()` function), even after `outer()` has finished executing.
* Every time `increment()` is called, it still has access to the `counter` variable from the **scope of `outer()`**, and the state of `counter` is preserved between calls.

### Key Points about Closures:

* Closures allow you to create functions with private data. The function retains access to variables that are "outside" its current scope.
* Closures are frequently used in scenarios such as **data encapsulation** (hiding private variables) and **callback functions** (where functions are passed and executed at a later time).

#### Example: Closure for Data Encapsulation (Private Variables)

```javascript
function createCounter() {
    let count = 0; // Private variable

    return {
        increment: function() {
            count++;
            console.log(count);
        },
        decrement: function() {
            count--;
            console.log(count);
        },
        getCount: function() {
            return count;
        }
    };
}

const counter = createCounter();
counter.increment(); // Logs 1
counter.increment(); // Logs 2
counter.decrement(); // Logs 1
console.log(counter.getCount()); // Logs 1
```

#### Explanation:

* The `count` variable is **private** to the `createCounter` function, but is accessible through the `increment`, `decrement`, and `getCount` methods.
* These methods form a **closure** around `count` and maintain its state, even though the `createCounter` function has finished executing.

