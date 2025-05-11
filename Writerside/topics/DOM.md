# DOM

# The HTML DOM (Document Object Model)
When a web page is loaded, the browser creates a `D`ocument `O`bject `M`odel of the page.

The `HTML DOM` model is constructed as a tree of `Objects`:
![image_4.png](image_4.png)

With the object model, JavaScript gets all the power it needs to create dynamic HTML:

* JavaScript can change all the HTML elements in the page
* JavaScript can change all the HTML attributes in the page
* JavaScript can change all the CSS styles in the page
* JavaScript can remove existing HTML elements and attributes
* JavaScript can add new HTML elements and attributes
* JavaScript can react to all existing HTML events in the page
* JavaScript can create new HTML events in the page

## What is the DOM?
The DOM is a W3C (World Wide Web Consortium) standard.

The DOM defines a standard for accessing documents:

"The W3C Document Object Model (DOM) is a platform and language-neutral interface that allows programs and scripts to dynamically access and update the content, structure, and style of a document."

The W3C DOM standard is separated into 3 different parts:

* Core DOM - standard model for all document types
* XML DOM - standard model for XML documents
* HTML DOM - standard model for HTML documents

## What is the HTML DOM?
The HTML DOM is a standard `object` model and `programming interface` for HTML. It defines:

* The HTML elements as `objects`
* The `properties` of all HTML elements
* The `methods` to access all HTML elements
* The `events` for all HTML elements

---

## HTML DOM Methods

* HTML DOM `methods` are actions you can perform (on HTML Elements).
* HTML DOM `properties` are values (of HTML Elements) that you can set or change.

> The document object represents your web page.
If you want to access any element in an HTML page, you always start with accessing the document object.
Below are some examples of how you can use the document object to access and manipulate HTML.

Here are tables and examples for the methods you've mentioned related to finding HTML elements, changing HTML elements, adding and deleting elements, and adding event handlers.

---

### 1. **Finding HTML Elements**

| Method                                  | Description                   | Example                                      |
| --------------------------------------- | ----------------------------- | -------------------------------------------- |
| `document.getElementById(id)`           | Find an element by element id | `document.getElementById("myId")`            |
| `document.getElementsByTagName(name)`   | Find elements by tag name     | `document.getElementsByTagName("div")`       |
| `document.getElementsByClassName(name)` | Find elements by class name   | `document.getElementsByClassName("myClass")` |

#### Example:

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

    <script>
        // Using getElementById
        let elementById = document.getElementById("myDiv");
        console.log(elementById.innerHTML);  // Outputs: Hello, World!

        // Using getElementsByTagName
        let divs = document.getElementsByTagName("div");
        console.log(divs[0].innerHTML);  // Outputs: Hello, World!

        // Using getElementsByClassName
        let elementsByClass = document.getElementsByClassName("myClass");
        console.log(elementsByClass[0].innerHTML);  // Outputs: Another div
    </script>
</body>
</html>
```

---

### 2. **Changing HTML Elements**

| Property/Method                          | Description                                   | Example                                        |
| ---------------------------------------- | --------------------------------------------- | ---------------------------------------------- |
| `element.innerHTML = newContent`         | Change the inner HTML of an element           | `element.innerHTML = "<p>New content</p>"`     |
| `element.attribute = newValue`           | Change the attribute value of an HTML element | `element.src = "newImage.jpg"`                 |
| `element.style.property = newStyle`      | Change the style of an HTML element           | `element.style.backgroundColor = "blue"`       |
| `element.setAttribute(attribute, value)` | Change the attribute value of an HTML element | `element.setAttribute("href", "newLink.html")` |

#### Example:

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
    
    <script>
        // Change innerHTML
        let contentDiv = document.getElementById("content");
        contentDiv.innerHTML = "New content added!";
        
        // Change image src
        let image = document.getElementById("image");
        image.src = "newImage.jpg";
        
        // Change background color style
        contentDiv.style.backgroundColor = "yellow";
        
        // Change href attribute
        let link = document.createElement("a");
        link.setAttribute("href", "https://newlink.com");
        link.innerHTML = "Visit New Link";
        document.body.appendChild(link);
    </script>
</body>
</html>
```

---

### 3. **Adding and Deleting Elements**

| Method                            | Description                                | Example                                       |
| --------------------------------- | ------------------------------------------ | --------------------------------------------- |
| `document.createElement(element)` | Create an HTML element                     | `let newDiv = document.createElement("div")`  |
| `document.removeChild(element)`   | Remove an HTML element from the DOM        | `parentElement.removeChild(childElement)`     |
| `document.appendChild(element)`   | Add an HTML element as a child             | `parentElement.appendChild(newElement)`       |
| `document.replaceChild(new, old)` | Replace an HTML element with another       | `parent.replaceChild(newElement, oldElement)` |
| `document.write(text)`            | Write directly into the HTML output stream | `document.write("<p>Hello World</p>")`        |

#### Example:

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

    <script>
        // Create a new element
        let newElement = document.createElement("p");
        newElement.innerHTML = "This is a new paragraph.";
        
        // Append new element to parent
        let parentDiv = document.getElementById("parentDiv");
        parentDiv.appendChild(newElement);
        
        // Remove an element
        let paragraphToRemove = parentDiv.getElementsByTagName("p")[0];
        parentDiv.removeChild(paragraphToRemove);
        
        // Replace an element
        let newElementToReplace = document.createElement("p");
        newElementToReplace.innerHTML = "This paragraph replaced the old one.";
        parentDiv.replaceChild(newElementToReplace, newElement);
        
        // Write content directly into HTML
        document.write("<h1>Page Loaded</h1>");
    </script>
</body>
</html>
```

---

### 4. **Adding Event Handlers**

| Method                                | Description                                | Example                                                                        |
| ------------------------------------- | ------------------------------------------ | ------------------------------------------------------------------------------ |
| `document.getElementById(id).onclick` | Add event handler code to an onclick event | `document.getElementById("myBtn").onclick = function() { alert("Clicked!"); }` |

#### Example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Adding Event Handlers</title>
</head>
<body>
    <button id="myBtn">Click me!</button>

    <script>
        // Add an onclick event handler to a button
        document.getElementById("myBtn").onclick = function() {
            alert("Button clicked!");
        };
    </script>
</body>
</html>
```

###### Explanation:

* When the button with `id="myBtn"` is clicked, it triggers the `onclick` event handler, which displays an alert box.
---

## HTML DOM Elements
### Finding HTML Elements
Often, with JavaScript, you want to manipulate HTML elements.

To do so, you have to find the elements first. There are several ways to do this:

* Finding HTML elements by id
* Finding HTML elements by tag name
* Finding HTML elements by class name
* Finding HTML elements by CSS selectors
* Finding HTML elements by HTML object collections

### Finding HTML Elements in JavaScript

In JavaScript, when you want to manipulate HTML elements, the first step is to **find** them in the DOM (Document Object Model). There are several methods available for finding elements, and each has its specific use cases.

---

### 1. **Finding HTML Elements by ID**

The easiest way to find a specific HTML element is by using the **element id**. Each element in an HTML document can have a unique `id` attribute, and you can use `document.getElementById()` to find that element.

#### Example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Finding Elements by ID</title>
</head>
<body>
    <div id="intro">This is the introduction section.</div>

    <script>
        // Finding element by id
        const element = document.getElementById("intro");

        // Check if element exists
        if (element) {
            console.log(element.innerHTML);  // Outputs: This is the introduction section.
        } else {
            console.log("Element not found.");
        }
    </script>
</body>
</html>
```

###### Explanation:

* The method `document.getElementById("intro")` finds the element with the `id="intro"`.
* If the element is found, it will be returned, and you can access its properties, such as `innerHTML`. If it's not found, it returns `null`.

---

### 2. **Finding HTML Elements by Tag Name**

You can use `document.getElementsByTagName()` to find all elements with a specific tag name. This method returns a **live HTMLCollection**, meaning it automatically updates if the DOM changes.

#### Example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Finding Elements by Tag Name</title>
</head>
<body>
    <p>This is a paragraph.</p>
    <p>This is another paragraph.</p>
    <div>Some content in a div.</div>

    <script>
        // Find all <p> elements
        const paragraphs = document.getElementsByTagName("p");

        // Loop through all paragraphs and log their content
        for (let i = 0; i < paragraphs.length; i++) {
            console.log(paragraphs[i].innerHTML);  // Outputs: This is a paragraph. and This is another paragraph.
        }
    </script>
</body>
</html>
```

###### Explanation:

* The method `document.getElementsByTagName("p")` returns all `<p>` elements in the document.
* You can loop through the resulting HTMLCollection to access each element.

---

### 3. **Finding HTML Elements by Class Name**

If you want to find elements that share the same class, use `document.getElementsByClassName()`. It returns a **live HTMLCollection** of elements with the specified class name.

#### Example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Finding Elements by Class Name</title>
</head>
<body>
    <div class="intro">This is the first intro section.</div>
    <div class="intro">This is the second intro section.</div>

    <script>
        // Find all elements with class "intro"
        const introElements = document.getElementsByClassName("intro");

        // Loop through all elements and log their content
        for (let i = 0; i < introElements.length; i++) {
            console.log(introElements[i].innerHTML);  // Outputs the content of both divs with class "intro"
        }
    </script>
</body>
</html>
```

###### Explanation:

* The method `document.getElementsByClassName("intro")` returns all elements that have the class name `intro`.
* It returns an HTMLCollection of elements, and you can loop through them to access each one.

---

### 4. **Finding HTML Elements by CSS Selectors**

The `document.querySelectorAll()` method allows you to find all elements that match a specified CSS selector. This gives you more flexibility, allowing you to find elements based on **id**, **class**, **attributes**, or **combinations** of those selectors.

#### Example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Finding Elements by CSS Selectors</title>
</head>
<body>
    <p class="intro">This is a paragraph with the class "intro".</p>
    <p class="intro">This is another paragraph with the class "intro".</p>
    <p>This is a regular paragraph without the "intro" class.</p>

    <script>
        // Find all <p> elements with class "intro"
        const introParagraphs = document.querySelectorAll("p.intro");

        // Loop through and log each element's content
        introParagraphs.forEach(function(paragraph) {
            console.log(paragraph.innerHTML);  // Outputs the two intro paragraphs
        });
    </script>
</body>
</html>
```

###### Explanation:

* The method `document.querySelectorAll("p.intro")` uses the CSS selector `p.intro` to find all `<p>` elements with the class `intro`.
* `querySelectorAll()` returns a **NodeList**, which can be iterated over using `forEach` or other array methods.

---
