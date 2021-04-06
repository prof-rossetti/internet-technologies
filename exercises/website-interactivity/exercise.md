# Website Interactivity Exercise

## Objectives

  1. Write JavaScript code to access and manipulate the contents of an HTML document.
  2. Write JavaScript code to add interactive features to a web page.
  2. Practice capturing HTML form inputs.

## Prerequisites

  1. ["Website Structure" Exercise](/exercises/website-structure/exercise.md)
  2. ["Website Style" Exercise](/exercises/website-style/exercise.md)

## References

### The Document Object Model (DOM)

Mozilla Guides:

  + [DOM Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
  + [Manipulating Documents](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents#the_document_object_model)

Professor's Notes:

  + [The Window Object](/notes/javascript/window.md) (including intervals, time-outs, and alerts)
  + [The Document Object](/notes/javascript/document.md) (including element selection and event-listeners)

### JavaScript Language

Mozilla Guides:

  + [JavaScript First Steps](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps)
  + [JavaScript Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)

W3Schools Guides:

  + [Intro to JavaScript](https://www.w3schools.com/js/js_intro.asp)
  + [Where to put JavaScript](https://www.w3schools.com/js/js_whereto.asp)
  + [Logging and Output](https://www.w3schools.com/js/js_output.asp)
  + [Variables](https://www.w3schools.com/js/js_variables.asp)
  + [Functions](https://www.w3schools.com/js/js_functions.asp)

Professor's Notes:
  + [JavaScript Language Overview](/notes/javascript/README.md)

## Instructions

Download this [example HTML page with a form elements and Twitter Bootstrap styling](/exercises/website-interactivity/bootstrap_5_form.html), or copy its contents into a new local HTML document. Locate the document and open it with your text editor. Preview the document in a browser. Notice the absence of interactive features. Follow the instructions below to add some interactivity.

### Button Click Events

Let's demonstrate our ability to respond to normal button click events:

```js
//
// BUTTON
//

var clickMeButton = document.getElementById("click-me")
//var clickCountSpan = document.getElementById("click-count")
//var clickCount = 0

function handleClick() {
  console.log("---------------------")
  console.log("YOU CLICKED ME!")
  //clickCount += 1
  //console.log("CLICK COUNT:", clickCount)
  //clickCountSpan.textContent = clickCount
}

clickMeButton.addEventListener("click", handleClick)
```

### Change Events

```js
//
// SELECT
//

var mySelect = document.getElementById("my-select")
console.log("DEFAULT SELECTION:", mySelect.value)

function handleSelection() {
  console.log("SELECTION:", mySelect.value)
}

mySelect.addEventListener("change", handleSelection)
```

### Radio, Check, and Switch Events

```js
//
// CHECKBOX
//

var myPref = document.getElementById("my-preference")

function handleCheck() {
  console.log("OPT OUT:", myPref.checked)
}

myPref.addEventListener("click", handleCheck, false)

//
// CHECKBOX (SWITCH)
//

var mySwitch = document.getElementById("my-switch")

function handleSwitch() {
  console.log("OPT OUT (SWITCH):", mySwitch.checked)
}

mySwitch.addEventListener("click", handleSwitch, false)

//
// RADIOS
//

var myRadioContainer = document.getElementById("my-radios-container")

function handleRadioToggle() {
  // h/t: https://stackoverflow.com/a/15839451
  var selectedRadio = document.querySelector('input[name="my-radio-preference"]:checked')
  console.log("----------------")
  console.log("RADIO TOGGLE:", selectedRadio.value)
}

myRadioContainer.addEventListener("click", handleRadioToggle, false)
```

### Form Submit Events

The form submit button is a special case of button click event:

```js
//
// FORM SUBMIT
//

var submitButton = document.getElementById("my-button")
//var emailInput = document.getElementById("my-email")
//var passwordInput = document.getElementById("my-password")
// etc...

function handleSubmit(event) {
  event.preventDefault() // because our button happens to be in a form, we prevent the default form action that would be triggered when the form is submitted

  console.log("---------------------")
  console.log("FORM SUBMIT...")
  //console.log("EMAIL:", emailInput.value)
  //console.log("PASSWORD:", passwordInput.value)
  // etc...
}

submitButton.addEventListener("click", handleSubmit)
```
