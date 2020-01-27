# Website Interactivity Exercise

## Objectives

  1. Use Twitter Bootstrap JavaScript plugins to add interactive features to a web page.
  2. Write your own JavaScript code to add interactive features to a web page.

## Prerequisites

  1. ["Website Structure" Exercise](/exercises/website-structure/exercise.md)
  2. ["Website Style" Exercise](/exercises/website-style/exercise.md)

## Reference

Twitter Bootstrap Interactive Components:

  + [Alerts](https://getbootstrap.com/docs/4.0/components/alerts/)
  + [Carousel](https://getbootstrap.com/docs/4.0/components/carousel/)
  + [Collapse](https://getbootstrap.com/docs/4.0/components/collapse/)
  + [Dropdowns](https://getbootstrap.com/docs/4.0/components/dropdowns)
  + [Modals](https://getbootstrap.com/docs/4.0/components/modal/)
  + [Tooltips](https://getbootstrap.com/docs/4.0/components/tooltips/)

W3Schools JavaScript Tutorial:

  + [Intro to JavaScript](https://www.w3schools.com/js/js_intro.asp)
  + [Where to put JavaScript](https://www.w3schools.com/js/js_whereto.asp)
  + [Logging and Output](https://www.w3schools.com/js/js_output.asp)
  + [Variables](https://www.w3schools.com/js/js_variables.asp)
  + [Functions](https://www.w3schools.com/js/js_functions.asp)
  + [Click Events](https://www.w3schools.com/js/js_events.asp)

Professor Rossetti's JavaScript Notes:

  + [JavaScript Language Overview](/notes/javascript/notes.md)
  + [The Window Object](/notes/javascript/window.md)
  + [The Document Object Model (DOM)](/notes/javascript/document-object-model.md)

## Instructions

### Setup

Create a new website project directory on your Desktop called something like "website-interactivity", and open it with your text editor.

Use the text editor to create a file inside this directory called "index.html" and place the following contents inside:

```html
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <title>Interactivity Exercise</title>
  </head>
  <body>

    <div class="container">
      <h1>My Home Page</h1>

      <!-- adapted from: https://getbootstrap.com/docs/4.0/components/dropdowns/ -->
      <div class="dropdown">
        <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
          My Dropdown Button
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <a class="dropdown-item" href="/">Home Page</a>
          <a class="dropdown-item" href="/page2.html">Second Page</a>
          <a class="dropdown-item" href="/page3.html">Third Page</a>
          <a class="dropdown-item" href="/page4.html">Fourth Page</a>
          <a class="dropdown-item" href="/stocks.html">Stocks Page</a>
        </div>
      </div>

      <footer>
        <hr>
        <p>This is a footer.</p>
      </footer>
    </div>

    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.4.1.slim.min.js" integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>
    <script>

      // FYI: this is JavaScript
      console.log("HELLO FROM THE HOME PAGE!")

    </script>
  </body>
</html>
```

Note the position of the `<script>` tags at the bottom of the `<body>`. This is the desired position for JavaScript tags for page-loading reasons. Functionality defined in these third-party JavaScript libraries makes the interactive functionality possible. And we add our custom JavaScript afterwards.

On the index page, you'll also notice hyperlinks to a few other pages: `page2.html`, `page3.html`, and `page4.html`. Let's create those other pages now, using the following content...

Page Two:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Page 2</title>
  </head>
  <body>
    <h1>My Second Page</h1>

    <div id="my-container">
      <p id="my-message">some placeholder content</p>
    </div>

    <script>

      // FYI: this is JavaScript
      console.log("HELLO FROM THE SECOND PAGE!")

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
  </body>
</html>
```

Page Three:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <!-- Material Design Icons -->
    <!-- see: http://google.github.io/material-design-icons/#icon-font-for-the-web -->
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

    <style>
      .material-icons.md-18 { font-size: 18px; }
    </style>

    <title>Page 3</title>
  </head>
  <body>
    <h1>My Third Page</h1>

    <!-- see: https://getbootstrap.com/docs/4.4/components/buttons/ -->
    <!-- see: https://material.io/resources/icons/?icon=shopping_cart&style=outline -->
    <button id="my-awesome-btn" type="button" class="btn btn-primary">
      Click Me <i class="material-icons md-18">shopping_cart</i>
    </button>

    <script>

      // FYI: this is JavaScript

      console.log("HELLO FROM THE THIRD PAGE!")

      var clickCount = 0

      // access the button element from the DOM by specifying its unique identifier
      var myBtn = document.getElementById("my-awesome-btn")

      // define a click event handler function
      function myBtnClick() {
        clickCount = clickCount + 1
        console.log("YOU CLICKED ME", clickCount, "TIMES! :-)")
      }

      // register the click event handler function to the button's click event
      myBtn.addEventListener("click", myBtnClick, false)

    </script>
  </body>
</html>
```

Page Four:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">

    <title>Page 4</title>
  </head>
  <body>
    <h1>My Fourth Page</h1>

    <select id="animal-selector">
      <option value="cat">Cat</option>
      <option value="dog">Dog</option>
      <option value="lion">Lion</option>
    </select>

    <script>

      // FYI: this is JavaScript
      console.log("HELLO FROM THE FOURTH PAGE!")

      // access the select element from the DOM by specifying its unique identifier
      var animalSelector = document.getElementById("animal-selector")

      // define a click event handler function
      function logSelectedAnimal(){
        console.log("YOU SELECTED:", animalSelector.value)
      }

      // register the click event handler function to the button's click event
      animalSelector.addEventListener("change", logSelectedAnimal, false)

    </script>
  </body>
</html>
```

Preview your website by either opening your "index.html" file with the browser, or navigating to your project directory from the command-line and starting up a local web server:

```sh
cd ~/Desktop/website-interactivity/
python -m http.server 8888
```

Examine the index file and observe the interactive features are enabled by specifying certain data attributes on the HTML elements, and by importing special pre-defined Twitter Bootstrap JavaScript plugins. Consult the Twitter Bootstrap reference links at the top of this document to add other interactive components like modals to your index page. Congratulations, you have unlocked the interactive features of the Twitter Bootstrap front-end framework!

Examine the second page, and inspect the element in your browser to view the JavaScript console, where you should see the "HELLO FROM THE SECOND PAGE!" message displayed. Examine the JavaScript in the file to see the `console.log` JavaScript statement, which is producing the desired effect. Also observe how we're able to write JavaScript to programmatically access and manipulate HTML elements.

Examine the third page, and inspect the element in your browser to view the JavaScript console, where you should see the "HELLO FROM THE THIRD PAGE!" message displayed. Click the button to see additional messages displayed. Examine the JavaScript in this file to see how to define and configure an event listener function to respond to button click events.

Examine the fourth page, and inspect the element in your browser to view the JavaScript console, where you should see the "HELLO FROM THE FOURTH PAGE!" message displayed. Select an option from the dropdown menu to see additional messages displayed. Examine the JavaScript in this file to see how to define and configure an event listener function to respond to selection change events, and to detect which option is selected.

Finally, if you are ready for a fun challenge, see the [Further Exploration Challenges](challenges.md).
