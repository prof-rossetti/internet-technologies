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

W3Schools Guides:

  + [The Document Object](https://www.w3schools.com/jsref/dom_obj_document.asp)
  + [DOM Element Objects](https://www.w3schools.com/jsref/dom_obj_all.asp)
  + [Accessing and Manipulating the DOM](https://www.w3schools.com/js/js_htmldom_document.asp)
  + [DOM Events](https://www.w3schools.com/js/js_htmldom_events.asp)

Mozilla Guides:

  + [DOM Introduction](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
  + [Event Listener API](https://developer.mozilla.org/en-US/docs/Web/API/EventListener)

Professor's Notes:

  + [The Window Object](/notes/javascript/window.md), including intervals, time-outs, and alerts
  + [The Document Object](/notes/javascript/document.md), including element selection and event-listeners

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

Download this [example HTML page with a form elements and Twitter Bootstrap styling](/exercises/website-interactivity/bootstrap_5_form.html), or copy its contents into a new local HTML document. Locate the document and open it with your text editor. Preview the document in a browser. Notice the absence of interactive features.

Let's demonstrate our ability to capture the values input into the form. Our goal will be to log the values into the JavaScript console when the user clicks the "Submit" button. We'll work through this in a number of steps (see sections below).

### Step 1: Event Listening


### Step 2: Accessing Form Inputs


```js
//
// TEXT INPUTS
//

var myEmail = document.getElementById("my-email")
var myPass = document.getElementById("my-password")
var myDate = document.getElementById("my-date")
var myColor = document.getElementById("my-color")
var myNumber = document.getElementById("my-number")
```

```js
//
// CHECKBOX
//

var myPref = document.getElementById("my-preference")

function handleCheck() {
  console.log("OPT OUT:", myPref.checked)
}

myPref.addEventListener("click", handleCheck, false)
```

```js
//
// CHECKBOX (SWITCH)
//

var mySwitch = document.getElementById("my-switch")

function handleSwitch() {
  console.log("OPT OUT (SWITCH):", mySwitch.checked)
}

mySwitch.addEventListener("click", handleSwitch, false)
```

```js
//
// RADIOS
//

var myRadioGroup = document.getElementById("my-radios")

function handleRadioToggle() {
  // h/t: https://stackoverflow.com/a/15839451
  var selectedRadio = document.querySelector('input[name="my-radio-group"]:checked')
  console.log("RADIO TOGGLE:", selectedRadio.value)
}

myRadioGroup.addEventListener("click", handleRadioToggle, false)
```

```js
//
// SELECT / DROP-DOWNS
//

var mySelect = document.getElementById("my-select")
console.log("DEFAULT SELECTION:", mySelect.value)

function handleSelection() {
  console.log("SELECTION:", mySelect.value)
}

mySelect.addEventListener("change", handleSelection)
```

```js

//
// BUTTON SUBMIT
//

var myBtn = document.getElementById("my-button")

function handleSubmit(event) {
  event.preventDefault() // because our button happens to be in a form, we prevent the default form action that would be triggered when the form is submitted

  console.log("---------------------")
  console.log("FORM SUBMIT...")

  console.log("EMAIL:", myEmail.value)
  console.log("PASSWORD:", myPass.value)
  console.log("DOB:", myDate.value)
  console.log("FAV COLOR:", myColor.value)
  console.log("LUCK NUMBER:", myNumber.value)

  console.log("OPT OUT:", myPref.checked)
  console.log("SELECTION:", mySelect.value)

}

myBtn.addEventListener("click", handleSubmit)
```
