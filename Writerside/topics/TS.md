# TS

* Typescript is nothing but a `superset` of JavaScript. It is built on top of javascript and introduces syntax enhancements. It brings support for `types` and `class-based object-oriented programming` paradigm to the world of Javascript. When compiled (or transpiled) it produces Javascript.
![image_5.png](image_5.png)
* Any `valid Javascript code` is also a `valid Typescript code`. It uses the same syntax and semantics as the javascript
* Typescript is `open source` and free to use. It is designed, developed and maintained by `Microsoft`.

## What TypeScript is not
Typescript is not a new programming language. It just a syntactic sugar added over Javascript. You can write pure javascript code and typescript still compiles it just as it is to Javascript.
![image_6.png](image_6.png)

If you know Javascript, the learning curve is very lean. If you are new to javascript, but coming from the c# or, Java background, you will see a lot of similarities in concept.

## Benefits of TypeScript
* Optional Type System
  TypeScript provides the static type system which provides great help in catching programming errors at compile time.
> Javascript is a dynamically typed system. The variables can hold any values. The type of variable is determined on the fly. The javascript implicitly converts types for example string to a number. This is ok for a small app, but large apps this can be a lot of headaches. It is difficult to test to see if the proper types are passed and errors always happen at runtime.
* Intellisense & syntax checking
  The static Type system helps in provide better tooling support in IDE. The intellisense, syntax checking & code completion are few of the major benefits you get with the tooling support. This speeds up the development time and also ensures that the programmers make fewer mistakes with typos. All the major editors like VSCode, atom, sublime text includes the tooling support for Typescript
* Maintainable code
  Typescript brings Types, Classes, interfaces & modules. it makes the code more maintainable and scalable. It much easier to organize the Typescript code, than a Javascript code
* Language Enhancement
  Typescript comes with several language features. It supports Encapsulation through classes and modules. Supports constructors, properties & functions. It has support for Interfaces. You can make use of Arrow functions or lambdas or anonymous functions

## Typescript Components
The architecture of TypeScript is neatly organized in different layers as shown in the image below. The three major layers are
![image_7.png](image_7.png)
* **Core TypeScript Compiler**: 
The TypeScript compiler manages the task of type-checking our code and converting it into valid JavaScript code. The compiler is made up of several different layers like core, program, scanner, parser, checker & emitter, etc
* **Typescript Standalone Compiler**(TSC) : 
The batch compilation CLI. Mainly handle reading and writing files for different supported engines (e.g. Node.js)
* **Typescript Language Services** : 
The Language Service supports the editors and other tools to provide better assistance in implementing features such as IntelliSense, code completion, formatting and outlining, colorization, code re-factoring like rename, Debugging interface helpers like validating breakpoints, etc.