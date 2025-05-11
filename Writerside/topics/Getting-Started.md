# Getting Started

This section shows how to start with JavaScript. We start with building a simple hello world example application. We will learn the basic syntax and rules and learn about identifiers and naming rules. etc. Later we look at what variables are and how to declare variables using let, var, and const.

## JavaScript Code Editors & IDE
We can write Javascript code in any editor. For example, you can use Notepad on Windows and Vim on Linux. But they are basic and provide only some unique features to make writing code faster.

## List of Code editors
When it comes to Javascript code editors, you have two choices: a `full-featured IDE` or `lightweight code editors`.
* Full Pledged IDE
  * [Webstorm](https://www.jetbrains.com/webstorm/)
* Light weight editors
  * [Visual Studio Code](https://code.visualstudio.com/)
  * Notepad++
  * Vim
* Online Code editors
  * JS Fiddle
  * StackBlitz
  * CodePen
  * JSbin
  * Gitpod

### Autocompletion   
Autocompletion is a feature that predicts the rest of the words that the user is typing. It is a must-have feature for a code editor. It reduces the time required to write code and lowers the risk of errors.
### Code organization
We must create different files and folders to organize the code as the application grows. The code editor must help us organize code into files and folders, making it easier to manage and maintain large codebases.
### Debugging tools
Another essential feature to consider when selecting a code editor is debugging tools. A good debugging tool assists developers in identifying and correcting code errors.

## Runtime Environment
JavaScript codes cannot run on their own. They need a runtime environment to run. Runtime is the environment in which a programming language executes.

Javascript can be run in runtime environments.

1. Browser Environment
2. Node Environment

### Browser Environment
#### The `<script>` Tag
In HTML, JavaScript code is inserted between `<script>` and `</script>` tags.

```HTML
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript in Body</h2>

<p id="demo"></p>

<script>
document.getElementById("demo").innerHTML = "My First JavaScript";
</script>

</body>
</html> 
```
### Node Environment
In node environment, you have to store your code in a myfirst.js file and run this file with node ie
```js
console.log("hello world")
```
and run the code as : 
```bash
C:\Users\Your Name>node myfirst.js
```

## JavaScript Keywords & Reserved Words
`JavaScript Keywords` have a special meaning in the context of a language. They are part of the `syntax of JavaScript`. These are reserved words and we cannot use them as `JavaScript Identifier names`. Using them will result in a compile error.

`arguments`	`await`	`break` `case`	`catch`	`class` `const`	`continue`	`debugger` `default`	`delete`	`do` `else`	`enum`	`export` `extends`	`false`	`finally` `for`	`function`	`get`
`if`	`import`	`in` `instanceof`	`new`	`null` `return`	`set`	`super` `switch`	`this`	`throw` `true`	`try`	`typeof` `var`	`void`	`while` `with`	`yield`	

### List of Strict Mode Reserved Words
You cannot use the following reserved keywords only if you enable strict mode.

For Example

The following works, although we used let as the variable name.
```js
let let=2;
console.log(let)          //2
```

But enabling the **`strict mode`** will result in an error.

```js
 
"use strict"
 
let let=2;                //Unexpected strict mode reserved word
console.log(let)      
```

The following is a list of **`strict mode-only`** reserve words.

`arguments`	`eval`	`implements` `interface`	`let`	`package` `private`	`protected`	`public` `static`	`yield`	