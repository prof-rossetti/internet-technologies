
# The Document Object

See also:
  + [The Document Object Model (DOM)](document-object-model.md)
  + [The Window Object](window.md)

The document is a property of the browser window object:

```js
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

Traversing the document tree hierarchy (we need to know about [JavaScript arrays](README.md#Arrays)):

```` js
document.childNodes
document.children
document.children[0].children
document.children[0].children[0]
document.children[0].children[1]
````

## Selections


Selecting elements:

  + [`document.getElementById()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById)
  + [`document.getElementsByClassName()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByClassName)
  + [`document.getElementsByTagName()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementsByTagName)
  + [`document.querySelector()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector)
  + [`document.querySelectorAll()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll)

```html
<div id="my-container">
  <p id="my-message">some placeholder content</p>
</div>
```

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

```html
<button id="my-awesome-btn">
  Click Me
</button>
```

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
