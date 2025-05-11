# Asynchronous TS

Asynchronous programming in TypeScript allows you to perform tasks that take time (like fetching data from a server, reading files, or waiting for user input) without blocking the main thread. While one task is being completed, JavaScript can continue running other code. TypeScript ensures that asynchronous operations are properly typed, improving both safety and readability.

---

### **1. Callbacks**

A **callback** is a function that is passed into another function as an argument and is executed after the task completes. While callbacks were the traditional way to handle asynchronous tasks in JavaScript, they can lead to "callback hell" if you have many nested callbacks.

#### Example: Using Callbacks

```ts
function fetchData(callback: (data: string) => void): void {
    setTimeout(() => {
        const data: string = "Fetched Data";
        callback(data);  // Callback function is called after 2 seconds
    }, 2000);
}

fetchData((result: string): void => {
    console.log(result);  // This will log "Fetched Data" after 2 seconds
});
```

#### Explanation:

* `fetchData` simulates an asynchronous operation using `setTimeout`.
* The callback function is passed as an argument to `fetchData` and is executed after 2 seconds, receiving the fetched data as an argument.

---

### **2. Promises**

A **Promise** is a modern way to handle asynchronous operations. A promise represents the eventual completion (or failure) of an asynchronous operation and allows for more readable code with `.then()` and `.catch()` methods for handling success or failure.

#### Example: Using Promises

```ts
function fetchData(): Promise<string> {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const data: string = "Fetched Data";
            resolve(data);  // Resolve the promise with data
        }, 2000);
    });
}

fetchData().then((result: string) => {
    console.log(result);  // This will log "Fetched Data" after 2 seconds
}).catch((error: Error) => {
    console.error(error);  // This will handle any errors
});
```

#### Explanation:

* `fetchData` returns a promise that resolves with the data `"Fetched Data"` after 2 seconds.
* The `.then()` method handles the result when the promise is successfully resolved.
* The `.catch()` method is used to handle any potential errors.

---

### **3. Async/Await**

The `async/await` syntax allows you to write asynchronous code in a more synchronous-looking style. It is built on top of promises and provides a cleaner and more readable way to handle asynchronous operations.

* **`async`**: Declares an asynchronous function.
* **`await`**: Pauses execution of the `async` function until the promise resolves.

#### Example: Using Async/Await

```ts
async function fetchData(): Promise<void> {
    const data: string = await new Promise((resolve) => {
        setTimeout(() => {
            resolve("Fetched Data");
        }, 2000);
    });
    console.log(data);  // This will log "Fetched Data" after 2 seconds
}

fetchData();
```

#### Explanation:

* The `fetchData` function is marked as `async`, allowing you to use `await` inside it.
* `await` pauses the function execution until the promise resolves with `"Fetched Data"`, making the code more readable than using `.then()` with promises.

---

### **Handling Errors with Async/Await**

With async/await, you can use `try/catch` blocks to handle errors more effectively.

```ts
async function fetchData(): Promise<void> {
    try {
        const data: string = await new Promise((resolve, reject) => {
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

* In case of an error (e.g., if the promise is rejected), the `catch` block catches the error and logs it.
* This makes error handling with `async/await` much cleaner than using `.catch()` in promises.

---

### **Example: Chaining Multiple Async Operations with Async/Await**

You can chain multiple asynchronous tasks using `async/await`. The operations are executed sequentially, and `await` ensures that each promise is resolved before continuing to the next one.

```ts
async function fetchData(): Promise<void> {
    const data1: string = await new Promise((resolve) => {
        setTimeout(() => resolve("Data 1"), 1000);
    });

    const data2: string = await new Promise((resolve) => {
        setTimeout(() => resolve("Data 2"), 1000);
    });

    console.log(data1, data2);  // This will log "Data 1 Data 2" after 2 seconds
}

fetchData();
```

#### Explanation:

* The first `await` ensures that `data1` is fetched before starting to fetch `data2`.
* The operations are sequential and readable, avoiding nested callbacks.

---

### **TypeScript Types for Asynchronous Operations**

In TypeScript, you can define types for asynchronous functions, including specifying the return type as `Promise<T>`.

#### Example: Defining Types for Async Functions

```ts
function fetchData(): Promise<string> {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Fetched Data");
        }, 2000);
    });
}

async function processData(): Promise<void> {
    const data: string = await fetchData();
    console.log(data);  // This will log "Fetched Data" after 2 seconds
}

processData();
```

In this example:

* The `fetchData()` function is typed to return a `Promise<string>`, meaning it will eventually resolve to a string value.
* The `processData()` function is an `async` function that returns `Promise<void>` and processes the result of `fetchData()`.

---

### **Conclusion**

Asynchronous programming in TypeScript allows you to handle operations that take time without blocking the main execution thread. TypeScript enhances JavaScript's async capabilities by adding strong typing, ensuring that your asynchronous operations are safe and predictable. Whether you're using callbacks, promises, or `async/await`, TypeScript ensures that your code is robust and type-safe, even in complex asynchronous scenarios.

* **Callbacks**: Functions passed as arguments and executed after a task completes.
* **Promises**: Represent the completion (or failure) of an asynchronous operation and allow chaining with `.then()` and `.catch()`.
* **Async/Await**: Provides a cleaner syntax for handling asynchronous operations and makes asynchronous code appear more synchronous.

By using **async/await** and **promises**, you can manage complex asynchronous tasks more easily while maintaining readability and type safety in TypeScript.
