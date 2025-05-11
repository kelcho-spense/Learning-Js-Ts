# DOM in TS

## To set up a Ts-Dom project

![image_9.png](image_9.png)

Certainly! Below is the full **TypeScript version** of the **HTML DOM (Document Object Model)** documentation, with both HTML and TypeScript code separated into respective `.html` and `.ts` files.

---

# The HTML DOM (Document Object Model) in TypeScript

The HTML DOM (Document Object Model) allows JavaScript to interact with web pages by representing them as a tree of objects. TypeScript provides type safety while manipulating these objects, ensuring that operations on HTML elements are correct and predictable.

---

### **What is the DOM?**

The **DOM** is a W3C (World Wide Web Consortium) standard that defines the structure of an HTML document as a tree of objects. JavaScript can access and manipulate these objects to modify the page dynamically.

The W3C DOM standard is split into three parts:

* **Core DOM**: A standard model for all document types (HTML, XML, etc.).
* **XML DOM**: A model for XML documents.
* **HTML DOM**: A model specifically for HTML documents.

---

### **HTML DOM Methods in TypeScript**

In TypeScript, you can manipulate HTML elements using various DOM methods. TypeScript helps by providing type annotations and ensuring the correct use of DOM methods.

---

### **1. Finding HTML Elements**

| Method                                  | Description                 | Example                                      |
| --------------------------------------- | --------------------------- | -------------------------------------------- |
| `document.getElementById(id)`           | Find an element by its `id` | `document.getElementById("myId")`            |
| `document.getElementsByTagName(name)`   | Find elements by tag name   | `document.getElementsByTagName("div")`       |
| `document.getElementsByClassName(name)` | Find elements by class name | `document.getElementsByClassName("myClass")` |

---

### **Finding HTML Elements by ID, Tag, and Class**

**HTML File: `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Finding Elements</title>
</head>
<body>
    <div id="myDiv">Hello, World!</div>
    <div class="myClass">Another div</div>

    <script src="app.js"></script>
</body>
</html>
```

**TypeScript File: `app.ts`**

```ts
// Finding elements by ID, Tag Name, and Class Name

const elementById: HTMLElement | null = document.getElementById("myDiv");
if (elementById) {
    console.log(elementById.innerHTML);  // Outputs: Hello, World!
}

const divs: HTMLCollectionOf<HTMLDivElement> = document.getElementsByTagName("div");
console.log(divs[0].innerHTML);  // Outputs: Hello, World!

const elementsByClass: HTMLCollectionOf<HTMLElement> = document.getElementsByClassName("myClass");
console.log(elementsByClass[0].innerHTML);  // Outputs: Another div
```

---

### **2. Changing HTML Elements**

| Property/Method                          | Description                                     | Example                                        |
| ---------------------------------------- | ----------------------------------------------- | ---------------------------------------------- |
| `element.innerHTML = newContent`         | Change the inner HTML of an element             | `element.innerHTML = "<p>New content</p>"`     |
| `element.attribute = newValue`           | Change the value of an attribute of an element  | `element.src = "newImage.jpg"`                 |
| `element.style.property = newStyle`      | Change the style of an HTML element             | `element.style.backgroundColor = "blue"`       |
| `element.setAttribute(attribute, value)` | Change the value of an HTML element's attribute | `element.setAttribute("href", "newLink.html")` |

---

### **Changing HTML Elements**

**HTML File: `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Changing HTML Elements</title>
</head>
<body>
    <div id="content">Original content</div>
    <img id="image" src="oldImage.jpg" alt="Old Image">

    <script src="app.js"></script>
</body>
</html>
```

**TypeScript File: `app.ts`**

```ts
// Change innerHTML
const contentDiv: HTMLElement | null = document.getElementById("content");
if (contentDiv) {
    contentDiv.innerHTML = "New content added!";  // Changes the content of the div
    contentDiv.style.backgroundColor = "yellow"; // Changes background color
}

// Change image src
const image: HTMLImageElement | null = document.getElementById("image") as HTMLImageElement;
if (image) {
    image.src = "newImage.jpg"; // Changes the image source
}

// Change href attribute for a link
const link: HTMLAnchorElement = document.createElement("a");
link.setAttribute("href", "https://newlink.com");
link.innerHTML = "Visit New Link";
document.body.appendChild(link); // Adds the link to the page
```

---

### **3. Adding and Deleting Elements**

| Method                            | Description                                      | Example                                       |
| --------------------------------- | ------------------------------------------------ | --------------------------------------------- |
| `document.createElement(element)` | Create a new HTML element                        | `let newDiv = document.createElement("div")`  |
| `document.removeChild(element)`   | Remove an HTML element from the DOM              | `parentElement.removeChild(childElement)`     |
| `document.appendChild(element)`   | Append an HTML element as a child of another     | `parentElement.appendChild(newElement)`       |
| `document.replaceChild(new, old)` | Replace an HTML element with another             | `parent.replaceChild(newElement, oldElement)` |
| `document.write(text)`            | Write content directly to the HTML output stream | `document.write("<p>Hello World</p>")`        |

---

### **Adding and Deleting Elements**

**HTML File: `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Adding and Deleting Elements</title>
</head>
<body>
    <div id="parentDiv">
        <p>This is a parent div.</p>
    </div>

    <script src="app.js"></script>
</body>
</html>
```

**TypeScript File: `app.ts`**

```ts
// Create a new element
const parentDiv: HTMLElement | null = document.getElementById("parentDiv");
if (parentDiv) {
    const newElement: HTMLParagraphElement = document.createElement("p");
    newElement.innerHTML = "This is a new paragraph.";
    parentDiv.appendChild(newElement); // Add the new paragraph to the div

    // Remove an element
    const paragraphToRemove: HTMLParagraphElement = parentDiv.getElementsByTagName("p")[0];
    parentDiv.removeChild(paragraphToRemove); // Remove the first paragraph

    // Replace an element
    const newElementToReplace: HTMLParagraphElement = document.createElement("p");
    newElementToReplace.innerHTML = "This paragraph replaced the old one.";
    parentDiv.replaceChild(newElementToReplace, newElement); // Replace the new paragraph
}

document.write("<h1>Page Loaded</h1>"); // Directly write content to the page
```

---

### **4. Adding Event Handlers**

| Method                                | Description                                | Example                                                                        |
| ------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------ |
| `document.getElementById(id).onclick` | Add an event handler to an `onclick` event | `document.getElementById("myBtn").onclick = function() { alert("Clicked!"); }` |

---

### **Adding Event Handlers**

**HTML File: `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Adding Event Handlers</title>
</head>
<body>
    <button id="myBtn">Click me!</button>

    <script src="app.js"></script>
</body>
</html>
```

**TypeScript File: `app.ts`**

```ts
// Add an onclick event handler to a button
const button: HTMLElement | null = document.getElementById("myBtn");
if (button) {
    button.onclick = function() {
        alert("Button clicked!");
    };
}
```

---
