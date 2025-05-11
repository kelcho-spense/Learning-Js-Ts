# Asynchronous Js

In JavaScript, **asynchronous programming** allows you to perform tasks that take time (like fetching data from a server, reading files, or waiting for user input) without blocking the main thread. This means that while one task is being completed, JavaScript can continue running other code.

JavaScript provides several ways to work with asynchronous operations, including **callbacks**, **Promises**, and **async/await**.

### 1. **Callbacks**

A **callback** is a function passed into another function as an argument and is executed after a task completes. Callbacks were the original way to handle asynchronous operations in JavaScript.

#### Example: Using Callbacks

```javascript
function fetchData(callback) {
    setTimeout(() => {
        const data = "Fetched Data";
        callback(data);  // Callback function is called after 2 seconds
    }, 2000);
}

fetchData(function(result) {
    console.log(result);  // This will log "Fetched Data" after 2 seconds
});
```

#### Explanation:

* The `fetchData` function simulates an asynchronous operation with `setTimeout`.
* After 2 seconds, the `callback` function is called with the data `"Fetched Data"`.
* This pattern is common for handling asynchronous tasks like reading files, making HTTP requests, etc.

However, callbacks can lead to **callback hell** when you have multiple nested callbacks, making the code harder to read and maintain.

### 2. **Promises**

A **Promise** is a more modern way to handle asynchronous operations. A promise represents the eventual completion (or failure) of an asynchronous operation. It allows you to attach `.then()` and `.catch()` methods to handle success or failure, respectively.

#### Example: Using Promises

```javascript
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const data = "Fetched Data";
            resolve(data);  // Resolve the promise with data
        }, 2000);
    });
}

fetchData().then(result => {
    console.log(result);  // This will log "Fetched Data" after 2 seconds
}).catch(error => {
    console.error(error);  // This will handle any errors
});
```

#### Explanation:

* The `fetchData` function returns a promise that resolves after 2 seconds with the data `"Fetched Data"`.
* The `.then()` method is used to handle the result when the promise is resolved successfully.
* The `.catch()` method is used to handle any potential errors (though there are none in this case).

### 3. **Async/Await**

`async/await` is a more readable and cleaner way to work with asynchronous code. It is built on top of Promises, allowing you to write asynchronous code in a more synchronous-looking style.

* **`async`**: Used to declare an asynchronous function.
* **`await`**: Used inside an async function to pause execution until the Promise resolves.

#### Example: Using Async/Await

```javascript
async function fetchData() {
    const data = await new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Fetched Data");
        }, 2000);
    });
    console.log(data);  // This will log "Fetched Data" after 2 seconds
}

fetchData();
```

#### Explanation:

* The `fetchData` function is marked as `async`, which allows us to use `await` inside it.
* `await` pauses the function execution until the promise resolves with the result `"Fetched Data"`.
* This approach is more readable than chaining `.then()` and `.catch()`, especially when dealing with multiple asynchronous operations.

### Handling Errors with Async/Await

You can use `try/catch` blocks to handle errors with async/await.

```javascript
async function fetchData() {
    try {
        const data = await new Promise((resolve, reject) => {
            setTimeout(() => {
                resolve("Fetched Data");
            }, 2000);
        });
        console.log(data);  // This will log "Fetched Data" after 2 seconds
    } catch (error) {
        console.error("Error:", error);
    }
}

fetchData();
```

#### Explanation:

* In case of an error (like if the promise is rejected), the `catch` block will catch the error and log it.

### Example: Chaining Multiple Async Operations with Async/Await

If you have multiple asynchronous tasks that depend on each other, you can chain them together with `async/await`.

```javascript
async function fetchData() {
    const data1 = await new Promise((resolve, reject) => {
        setTimeout(() => resolve("Data 1"), 1000);
    });

    const data2 = await new Promise((resolve, reject) => {
        setTimeout(() => resolve("Data 2"), 1000);
    });

    console.log(data1, data2);  // This will log "Data 1 Data 2" after 2 seconds
}

fetchData();
```

#### Explanation:

* The `await` keyword ensures that `data2` will not be fetched until `data1` is successfully retrieved.
* The asynchronous operations are handled sequentially, making the code easier to read compared to using `.then()` with promises.

