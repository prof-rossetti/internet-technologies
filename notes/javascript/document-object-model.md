# The Document Object Model (DOM)

> "The Document Object Model (DOM) is the data representation of the objects that comprise the structure and content of a document on the web." - [Mozilla](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)

> "When an HTML document is loaded into a web browser, it becomes a document object." - [W3Schools](https://www.w3schools.com/js/js_htmldom_document.asp)

## References

W3Schools Guides:

  + [The Document Object](https://www.w3schools.com/jsref/dom_obj_document.asp)
  + [DOM Element Objects](https://www.w3schools.com/jsref/dom_obj_all.asp)
  + [Accessing and Manipulating the DOM](https://www.w3schools.com/js/js_htmldom_document.asp)
  + [DOM Events](https://www.w3schools.com/js/js_htmldom_events.asp)

Mozilla Guides:

  + [DOM Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
  + [Event Listener API](https://developer.mozilla.org/en-US/docs/Web/API/EventListener)

## Accessing and Manipulating the DOM

The browser window object, and some properties:

```js
window.innerHeight
window.innerWidth

window.document
```

The document object and some properties:

```js
document

document.head
document.body

document.title
document.URL
document.cookie
```

Traversing the document tree hierarchy (we need to know about JavaScript arrays):

```` js
document.childNodes
document.children
document.children[0].children
document.children[0].children[0]
document.children[0].children[1]
````

Selecting elements:

  + `document.getElementById()`
  + `document.getElementsByTagName()`
  + `document.getElementsByClassName()`
  + `document.querySelectorAll()`

```html
<div id="my-container">
  <p id="my-message">some placeholder content</p>
</div>
```

```js
// select elements from the DOM by specifying their unique identifiers:
var myDiv = document.getElementById("my-container")
var myParagraph = document.getElementById("my-message")

// manipulate properties of an element:
myParagraph.innerHTML = "Fun times!"
myParagraph.style.color = "red"

// can even create new elements:
var myHeading = document.createElement("h3")
myHeading.innerHTML = "This is a heading"
myDiv.appendChild(myHeading)
```

#### Event-listening

References:

  + https://developer.mozilla.org/en-US/docs/Web/API/EventListener
  + https://www.w3schools.com/jsref/met_document_addeventlistener.asp

```html
<button id="my-awesome-btn">
  Click Me
</button>
```

```js
var clickCount = 0

// access the button element from the DOM by specifying its unique identifier
var myBtn = document.getElementById("my-awesome-btn")

// define a click event handler function
function myBtnClick() {
  clickCount = clickCount + 1
  console.log("YOU CLICKED ME", clickCount, "TIMES! :-)")
}

// register the handler function to the button's click event
myBtn.addEventListener("click", myBtnClick, false)
```
