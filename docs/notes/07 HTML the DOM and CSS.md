---
id: b1wmvxvi7siz4gujx6s6yt5
title: 07 HTML the DOM and CSS
desc: ""
updated: 1713096813447
created: 1712946299586
---

## HTML

### Creating an HTML Document

- see code/Chapter 07/helloworld.html

### Understanding Nested Relationships

- see code/Chapter 07/helloworld.html

## The Document Object Model

- Created when browser loads the HTML file
  - internal model of elements - the DOM
    - a dynamic model of the page
      - can be modified with JavaScript directly in the browser (without altering the underlying html code)
        - the key to dynamic web apps
  - a series of nested boxes:
    html box - contains:
    head box - contains:
    title box
    body box - new box - contains:
    h1 box - and:
    p box
- parent-child relationships between the elements are the key to the DOM

### The DOM API

- JavaScript modifies the DOM in a web browser using the DOM API
  - any change is generally instantly visible on the page
    - instant visual feedback to the viewer
  - API provides a series of methods for making these modifications
    - many on the document object:
      - document.title returns/sets the title for the current page

### Element Identifiers

- to modify elements, we need to be able to access them from code
- many ways in JavaScript
  - simplest is using id attribute - a unique identifier for an element

```js
//helloworld.html
let heading = document.getElementByID("main-heading");
heading;
//<h1 id="main-heading">Hello!</h1>
```

- now that we have the heading as a variable, we can operate on it:

```js
heading.innerText;
//'Hello!'
heading.innerText = "Hi there...";
//'Hi there...'
```

- _id_.innerText can both return and change the text in the element
  - but remember it only changes the DOM, not the underlying html
    - if you refresh, the changes will disappear

## Script Elements

- add JavaScript to an HTML file using the script HTML element:
  - either within tags directly in the html file...
    - keeps everything in one place
  - or as a link to a separate JavaScript file (as with an external stylesheet)
    - allows script to be used for multiple pages
    - more manageable for larger projects

## CSS

- see code/Chapter 7/index.html

### Link Elements

- see code/Chapter 7/index.html

### Rulesets

- see code/Chapter 7/style.css

### Selectors

- see code/Chapter 7/style.css

## Using CSS Selectors in JavaScript

- some DOM methods rely on CSS selector syntax to select elements from the DOM
  - document.querySelectorAll(_selector_):
    - takes string containing CSS selector
    - returns array-like object with all elements matching selector:

```js
document.querySelectorAll(".highlight"); //to find all elements with the class "highlight"
//>Nodelist(2) [p.highlight], p.highlight - returns a Nodelist (no. of elements matching selector) [elements]

let strong = document.querySelectorAll(#main-heading strong); // to find all strong elements with a parent element with main-heading ID
strong;
//>Nodelist [strong] - only one element matches the selector (so no number returned)
strong[0].textContent; // get the text of that element (zero-indexing so you need 0 to select the first (and only) element here)
```
