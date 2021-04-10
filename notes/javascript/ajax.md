# Asynchronous JavaScript (AJAX)

> AJAX stands for Asynchronous JavaScript and XML. In a nutshell, it is the use of the XMLHttpRequest object to communicate with server-side scripts. It can send as well as receive information in a variety of formats, including JSON, XML, HTML, and even text files. AJAX’s most appealing characteristic is its "asynchronous" nature which means it can communicate with the server, exchange data, and update the page all without having to refresh the browser.
>
> The two major features of AJAX allow you to do the following:
>
>  + Make requests to the server without reloading the page
>  + Receive and work with data from the server
>
> ... - [Mozilla website](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)

Use AJAX to send and receive data between your client-side script and a server, all done without refreshing the page.

Be careful not to assume synchronous execution of your JavaScript code. Assume the time between request and response is not certain.

Don't be surprised if you don't have access to the response variable within the global scope unless you pass it there from within the request function. For more information, refer to this guide on [global vs local scopes](https://www.w3schools.com/js/js_scope.asp).

## How to Make an AJAX Request

Use vanilla JavaScript, jQuery, or d3 to make requests. Some libraries offer shortcut/alias methods specifically used for making GET requests for JSON data.

> NOTE: we are going to want to use the Vanilla JavaScript fetch() method if possible, unless we're already using those other dependencies, to avoid unnecessary dependencies.

### Vanilla JavaScript

References:

  + [Using Fetch - Mozilla](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
  + [`fetch()`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
  + [`Promise`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
  + [`Response`](https://developer.mozilla.org/en-US/docs/Web/API/Response)

Issuing GET requests (the following approaches are equivalent):

```` js
var requestUrl = "https://example.com/api/robots.json"

// SHORTEST WAY (PROMISE CHAINING)

fetch(requestUrl)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(err => console.log(err))

// SHORT WAY (PROMISE CHAINING)

fetch(requestUrl)
    .then(response => {
        console.log("RESPONSE", response)
        return response.json()
    })
    .then(data => {
        console.log("DATA", data)
    })
    .catch(function (err) {
        console.error("FETCH ERR", err)
    })
````


Issuing POST requests:

```` js
var requestUrl = "https://example.com/api/robots"
var formData = {name: "New Bot", description: "Does all the things."}
var requestOptions = {
  method: "POST",
  headers: {'Accept':'application/json', 'Content-Type':'application/json'},
  body: JSON.stringify(formData)
}

fetch(requestUrl, requestOptions)
  .then(function(response) {
    if (response.ok) { // check response status and proceed accordingly
      response.json()
        .then(function(data){
          console.log(data)
        })
    } else {
      console.log("OOPS")
    }
  })
  .catch(function(err){
    console.log("OOPS")
  })
````

### D3

References:

  + [`d3.request()`](https://github.com/d3/d3-request/blob/master/README.md#api-reference).
  + [`d3.json()`](https://github.com/d3/d3-request/blob/master/README.md#json)

Issuing GET requests with D3:

```` js
var url = "https://raw.githubusercontent.com/SCSU-CSC-Department/201701-csc-443-01/master/course.json"

d3.json(url, function(json){
  console.log("GOT SOME DATA:", json)
  // DO SOMETHING WITH THE DATA HERE!
})
````

Issuing POST requests with D3:

```` js
var requestUrl = "https://southernct-443-robots-api.herokuapp.com/api/robots"
var formData = {name: "New Bot", description: "Does all the things."}

d3.request(requestUrl)
  .header("Accept", "application/json")
  .header("Content-Type", "application/json")
  .on("error", function(error) {
    // HANDLE ERRORS HERE
  })
  .on("load", function(xhr) {
    // HANDLE RESPONSE HERE
  })
  .send("POST", JSON.stringify(formData))
````


### JQuery

References:

  + [`$.ajax()`](http://api.jquery.com/jquery.ajax/)
  + [`$.getJSON()`](http://api.jquery.com/jquery.getjson/)
  + [`$.post()`](https://api.jquery.com/jquery.post/)
  + [`jqXHR`](https://api.jquery.com/jQuery.ajax/#jqXHR)

Issuing GET requests with JQuery:

```` js
var url = "https://raw.githubusercontent.com/SCSU-CSC-Department/201701-csc-443-01/master/course.json"

$.getJSON(url, function(json) {
  console.log("GOT SOME DATA:", json)
  // DO SOMETHING WITH THE DATA HERE!
});
````

Issuing POST requests with JQuery:

```` js
var requestUrl = "https://southernct-443-robots-api.herokuapp.com/api/robots"
var formData = {name: "New Bot", description: "Does all the things."}

$.post(requestUrl, formData)
  .done(function(data, textStatus, xhr) {
    // HANDLE RESPONSE HERE
  })
  .fail(function(xhr, textStatus, errorThrown){
    // HANDLE ERRORS HERE
  })

````
