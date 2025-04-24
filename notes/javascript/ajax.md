# Asynchronous JavaScript (AJAX)

> AJAX stands for Asynchronous JavaScript and XML. In a nutshell, it is the use of the XMLHttpRequest object to communicate with server-side scripts. It can send as well as receive information in a variety of formats, including JSON, XML, HTML, and even text files. AJAX’s most appealing characteristic is its "asynchronous" nature which means it can communicate with the server, exchange data, and update the page all without having to refresh the browser.
>
> The two major features of AJAX allow you to do the following:
>
>  + Make requests to the server without reloading the page
>  + Receive and work with data from the server
>
> ... - [Mozilla website](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)

Use AJAX to send and receive data on the client-side, without refreshing the page.

Be careful not to assume synchronous execution of your JavaScript code. Assume the time between request and response is not certain.

After fetching the data, it won't be accessible to the console or other global scope part of your program (unless you save the results to a variable previously defined in the global scope). For more information, refer to this guide on [global vs local scopes](https://www.w3schools.com/js/js_scope.asp).

When we make an asynchronous request, we'll be working with objects called [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise), so it will be helpful to read up about them. To make use of the data eventually returned in a Promise, we'll either use a `then()` strategy (preferred), or an async/await strategy (might not work on older browsers).



## How to Make an AJAX Request

To make an asyncronous HTTP request, we can either use vanilla JavaScript, or third-party packages like d3, jQuery, or axios.

> NOTE: let's prefer to use the vanilla JavaScript `fetch()` method if possible, unless we're already using one of the other packages in our project, to avoid unnecessary dependencies.

> UPDATE: for beginners, it might be a lot easier to use the `d3` package than Vanilla JavaScript, and you might find this dependency is worth it.

### Vanilla JavaScript

References:

  + [Using Fetch - Mozilla](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
  + [`fetch()`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
  + [`Promise`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
  + [`Response`](https://developer.mozilla.org/en-US/docs/Web/API/Response)

Issuing GET requests (the following approaches are equivalent):

```` js
var requestUrl = "https://raw.githubusercontent.com/prof-rossetti/internet-technologies/main/exercises/fetch-the-data/gradebook.json"

// PROMISE CHAINING w/ ARROW FUNCTIONS

fetch(requestUrl)
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(err => console.log(err))

// PROMISE CHAINING

fetch(requestUrl)
    .then(response => {
        console.log("RESPONSE", response)
        return response.json()
    })
    .then(data => {
        console.log("DATA", data) // this is the data you're looking for
    })
    .catch(err => {
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

As you can see, these methods are a bit verbose, so it might be easier to use a library like `d3` instead.

### D3

References:

  + [`d3-fetch`](https://d3js.org/d3-fetch)
  + [`d3.json()`](https://d3js.org/d3-fetch#json)
  + [`d3.csv()`](https://d3js.org/d3-fetch#csv)

We can use the `d3-fetch` sub-library of [`d3`](./packages/d3.md) to fetch data. When fetching JSON formatted data, we use `d3.json()`. When fetching CSV formatted data, we use `d3.csv()`.


Issuing GET requests with D3 (for JSON and CSV data, respectively):

```` js
// FETCHING JSON DATA
var requestUrl = "https://raw.githubusercontent.com/prof-rossetti/intro-to-python/refs/heads/main/data/gradebook.json"

d3.json(requestUrl, function(data){
  console.log("GOT SOME DATA:", data)
  // DO SOMETHING WITH THE DATA HERE!
})
````

```` js
// FETCHING CSV DATA
var requestUrl = "https://raw.githubusercontent.com/prof-rossetti/intro-to-python/refs/heads/main/data/gradebook.csv"

d3.csv(requestUrl, function(data){
  console.log("GOT SOME DATA:", data)
  // DO SOMETHING WITH THE DATA HERE!
})
````

Issuing POST requests with D3:

```` js
var requestUrl = "https://httpbin.org/post"
var formData = {
  name: "Waldo Ma",
  email: "waldo@example.com",
  age: 75
}
var requestOptions = {
  method: "POST", 
  headers: {"Content-Type": "application/json"},
  body: JSON.stringify(formData)
}

d3.json(requestUrl, requestOptions)
.then(response => {
  console.log("SUCCESS:", response)
  // DO SOMETHING WITH THE RESPONSE HERE!

})
.catch(error => {
  console.error("ERROR:", error)
})
````

<hr>

### JQuery

> 2025 NOTE: we don't really use JQuery anymore.

References:

  + [`$.ajax()`](http://api.jquery.com/jquery.ajax/)
  + [`$.getJSON()`](http://api.jquery.com/jquery.getjson/)
  + [`$.post()`](https://api.jquery.com/jquery.post/)
  + [`jqXHR`](https://api.jquery.com/jQuery.ajax/#jqXHR)

Issuing GET requests with JQuery:

```` js
var url = "https://raw.githubusercontent.com/prof-rossetti/internet-technologies/main/exercises/fetch-the-data/gradebook.json"

$.getJSON(url, function(json) {
  console.log("GOT SOME DATA:", json)
  // DO SOMETHING WITH THE DATA HERE!
});
````

Issuing POST requests with JQuery:

```` js
var requestUrl = "https://example.com/api/robots"
var formData = {name: "New Bot", description: "Does all the things."}

$.post(requestUrl, formData)
  .done(function(data, textStatus, xhr) {
    // HANDLE RESPONSE HERE
  })
  .fail(function(xhr, textStatus, errorThrown){
    // HANDLE ERRORS HERE
  })

````

### Axios

References:

  + [Axios Docs](https://axios-http.com/)
  + [Axios Source Code](https://github.com/axios/axios)

Issuing GET requests with axios:

``` js
var requestUrl = "https://raw.githubusercontent.com/prof-rossetti/internet-technologies/main/exercises/fetch-the-data/gradebook.json"

axios.get(requestUrl)
    .then(function (response) {
        // handle success
        console.log("RESPONSE:", response)
        console.log("DATA:", response.data)
    })
    .catch(function (error) {
        // handle error
        console.log(error)
    })
    .then(function () {
        // always executed
    })

```

Issuing GET requests with URL params object (as an alternative to compiling the params in the request URL itself, which would require some escaping of spaces and special characters), with Axios:

```js
var API_KEY = "abc123" // TODO: use env vars or session storage instead of hard-coding

// https://www.yelp.com/developers/documentation/v3/business_search
var requestUrl = "https://api.yelp.com/v3/businesses/search"
console.log("REQUEST URL:", requestUrl)

var requestOptions = {
    headers: {
        Authorization: `Bearer ${API_KEY}`,
    },
    params: {
      location: "Washington, DC", 
      price: 3 
    }
}
console.log("REQUEST OPTIONS:", requestOptions)

axios.get(requestUrl, requestOptions)
  .then(function (response) {
    //console.log("RESPONSE:", response)
    console.log("DATA:", response.data)
  })
  .catch(function (error) {
    console.log("ERR:", error)
  })
  .then(function () {
    console.log("DONE...")
  })
})
```

Issuing POST requests with axios:

```js
var requestUrl = "https://example.com/api/robots"
var requestData = {
    firstName: 'Fred',
    lastName: 'Flintstone'
}
axios.post(requestUrl, requestData)
  .then(function (response) {
    console.log(response)
  })
  .catch(function (error) {
    console.log(error)
  })
```


## Async / Await

References:
  + [Async Function - Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
  + [Async / Await - Mozilla](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await)
  + [Async / Await - W3Schools](https://www.w3schools.com/js/js_async.asp)

FYI: sometimes instead of using `then()` to handle Promises, you might see an async / await strategy:

```js
function resolveAfter2Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved')
    }, 2000)
  });
}

async function asyncCall() {
    const result = await resolveAfter2Seconds()
    console.log(result);
}

asyncCall()

```

> NOTE: The await keyword can only be used inside an async function. So it might require us to use some awkward wrapper function(s).
