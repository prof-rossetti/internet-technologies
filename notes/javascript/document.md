
# The Document Object

See also:
  + [The Document Object Model (DOM)](document-object-model.md)
  + [The Window Object](window.md)

The document is a property of the browser window object:

```js
window.document
```

The document object allows us to programmatically reference parts of the HTML document, including the `<head>`, `<body>`, and other properties:

```js
document

document.head
document.body

document.title
document.URL
document.cookie
```

We can traverse the document tree hierarchy by referencing child nodes (it helps to know about [arrays](./datatypes/arrays.md) first):

```` js
document.childNodes
document.children
document.children[0].children
document.children[0].children[0]
document.children[0].children[1]
````

## Selections

We can also use the document to access and manipulate specific elements on the page, using a handful of different selector methods:

  + [`document.getElementById()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
  + [`document.getElementsByClassName()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
  + [`document.getElementsByTagName()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByTagName)
  + [`document.querySelector()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
  + [`document.querySelectorAll()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)

For example, if we have this HTML content on a page:

```html
<div id="my-container">
  <p id="my-message">some placeholder content</p>
</div>
```

We can write this JavaScript to programmatically reference and manipulate these elements:

```html
<script type="text/javascript">

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

</script>
```

## Event-listening

References:

  + https://developer.mozilla.org/en-US/docs/Web/API/EventListener
  + https://www.w3schools.com/jsref/met_document_addeventlistener.asp

We can use event listeners to respond to certain events such as button clicks, dropdown selections, etc.

For example if we have this HTML button element on the page:

```html
<button id="my-awesome-btn">
  Click Me
</button>
```

We can write this JavaScript to reference the button element and take certain actions once the button is clicked:

```html
<script type="text/javascript">

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

</script>
```
