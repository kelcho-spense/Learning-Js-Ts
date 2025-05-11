# JSON

* JSON stands for JavaScript Object Notation 
* JSON is a text format for storing and transporting data 
* JSON is "self-describing" and easy to understand

## JSON Example
This example is a JSON string:
```json
{"name" : "John", "age" : 30, "car" : null}
```
## JSON Data Types
In JSON, values must be one of the following data types:

* a `string`
* a `number`
* an `object (JSON object)`
* an `array`
* a `boolean`
* `null`

> JSON values cannot be one of the following data types:
> * a `function`
> * a `date`
> * `undefined`

- `Strings` in JSON must be written in double quotes.
```JSON
{"name" : "John"}
```
- `Numbers` in JSON must be an integer or a floating point.
```JSON
{"age" : 30}
```
- Values in JSON can be `objects`.
```JSON
{
    "employee" : {
      "name" : "John", 
      "age" : 30, 
      "city" : "New York"
    }
}
```
- Values in JSON can be `arrays`.
```JSON
{
"employees" : ["John", "Anna", "Peter"]
}
```
- Values in JSON can be `Boolean(true/false)`.
```JSON
{"sale" : true}
```
- Values in JSON can be `null`.
```JSON
{"middlename" : null}
```
## JSON Methods
### JSON.parse()
A common use of JSON is to exchange data to/from a web server.
When receiving data from a web server, the data is always a string.
Parse the data with `JSON.parse()`, and the data becomes a JavaScript object.
#### Example 
Imagine we received this text from a web server:
```JSON
'{"name":"John", "age":30, "city":"New York"}'
```
Use the JavaScript function `JSON.parse()` to convert text into a JavaScript object:
```js
const obj = JSON.parse('{"name":"John", "age":30, "city":"New York"}');
```

### JSON.stringify()
A common use of JSON is to exchange data to/from a web server.
When sending data to a web server, the data has to be a string.
You can convert any JavaScript datatype into a string with `JSON.stringify()`.

Imagine we have this object in JavaScript:
```js
const obj = {name: "John", age: 30, city: "New York"};
```
Use the JavaScript function `JSON.stringify()` to convert it into a string.
```js
const myJSON = JSON.stringify(obj);
```
> The result will be a string following the JSON notation.
myJSON is now a string, and ready to be sent to a server: