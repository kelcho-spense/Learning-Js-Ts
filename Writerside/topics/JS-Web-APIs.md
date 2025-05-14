# JS Web APIs

### What is Web API?

API stands for **Application Programming Interface**.

A **Web API** is an application programming interface for the Web.

* A **Browser API** can extend the functionality of a web browser.
* A **Server API** can extend the functionality of a web server.

---

### Browser APIs

All browsers have a set of built-in Web APIs to support complex operations, and to help in accessing data.
For example, the **Geolocation API** can return the coordinates of where the browser is located.

---

### Web Storage API

The **Web Storage API** provides a simple syntax for storing and retrieving data in the browser.

---

#### The localStorage Object

The `localStorage` object provides access to a local storage for a particular web site.
It allows you to **store**, **read**, **add**, **modify**, and **delete** data items for that domain.

**setItem() Method**

```javascript
localStorage.setItem("name", "John Doe");
```

**getItem() Method**

```javascript
localStorage.getItem("name");
```

**removeItem() Method**

```javascript
localStorage.removeItem("name");
```

---

#### The sessionStorage Object

The `sessionStorage` object is identical to the `localStorage` object.
The difference is that the `sessionStorage` object stores data **for one session only**.

The data is deleted when the browser is closed.

**setItem() Method**

```javascript
sessionStorage.setItem("name", "John Doe");
```

**getItem() Method**

```javascript
sessionStorage.getItem("name");
```

---

### IndexedDB API

The **IndexedDB API** is a **low-level** API for storing large amounts of structured data, including files and blobs.

It is more powerful than `localStorage` and allows for **transactions**, **indexing**, and **searching** within data.

---

#### Opening a Database

```javascript
let request = indexedDB.open("MyDatabase", 1);
```

#### Creating an Object Store

```javascript
request.onupgradeneeded = function(event) {
  let db = event.target.result;
  db.createObjectStore("users", { keyPath: "id" });
};
```

#### Adding Data

```javascript
request.onsuccess = function(event) {
  let db = event.target.result;
  let transaction = db.transaction(["users"], "readwrite");
  let store = transaction.objectStore("users");
  store.add({ id: 1, name: "John Doe", email: "john@example.com" });
};
```

#### Retrieving Data

```javascript
let transaction = db.transaction(["users"]);
let store = transaction.objectStore("users");
let getRequest = store.get(1);

getRequest.onsuccess = function() {
  console.log(getRequest.result);
};
```

---

### Fetch API

The **Fetch API** provides a modern interface for fetching resources across the network.
It returns **Promises**, making it easier to work with asynchronous requests.

---

#### GET Request

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error('Error:', error));
```

#### POST Request

```javascript
fetch('https://api.example.com/data', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ name: 'John Doe' })
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```

---

### Clipboard API

The **Clipboard API** allows you to interact with the clipboard for reading and writing text.
Useful for copy-paste functionality in web applications.

---

#### Writing to Clipboard

```javascript
navigator.clipboard.writeText("Copied to clipboard!")
  .then(() => {
    console.log("Text copied!");
  })
  .catch(err => {
    console.error("Failed to copy: ", err);
  });
```

#### Reading from Clipboard

```javascript
navigator.clipboard.readText()
  .then(text => {
    console.log("Pasted text: ", text);
  })
  .catch(err => {
    console.error("Failed to read clipboard: ", err);
  });
```

---

### Other Common Browser APIs

* **Canvas API** – Allows drawing and rendering of graphics on a web page.
* **WebSocket API** – Enables real-time two-way communication with a server.
* **Notification API** – Allows web apps to send notifications to the user's desktop or device.
* **WebRTC API** – Supports real-time communication (audio, video, and data sharing).
* **Drag and Drop API** – Enables drag-and-drop functionality within web pages.
* **Vibration API** – Provides access to device vibration hardware (mostly mobile devices).
* **Battery Status API** – Gives information about the device’s battery status (deprecated on some platforms).

---