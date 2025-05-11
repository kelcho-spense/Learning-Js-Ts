# JS Web APIs

What is Web API?
* API stands for Application Programming Interface.
* A Web API is an application programming interface for the Web.
* A Browser API can extend the functionality of a web browser.
* A Server API can extend the functionality of a web server.

## Browser APIs
All browsers have a set of built-in Web APIs to support complex operations, and to help accessing data.
For example, the Geolocation API can return the coordinates of where the browser is located.

### Web Storage API
The Web Storage API is a simple syntax for storing and retrieving data in the browser. It is very easy to use:

- ### The localStorage Object
The localStorage object provides access to a local storage for a particular Web Site. It allows you to store, read, add, modify, and delete data items for that domain.

#### The setItem() Method
The `localStorage.setItem()` method stores a data item in a storage.
```js
localStorage.setItem("name", "John Doe");
```
#### The getItem() Method
The `localStorage.getItem()` method retrieves a data item from the storage.
```js
localStorage.getItem("name");
```
#### removeItem() method
```js
localStorage.removeItem("name");
```
- ### The sessionStorage Object
The sessionStorage object is identical to the localStorage object.
The difference is that the sessionStorage object stores data for one session.
> The data is deleted when the browser is closed.

#### The setItem() Method
The `sessionStorage.setItem()` method stores a data item in a storage.
It takes a name and a value as parameters:
```js
sessionStorage.setItem("name", "John Doe");
```
#### The getItem() Method
The `sessionStorage.getItem()` method retrieves a data item from the storage.
It takes a name as parameter:
