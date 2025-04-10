# The Browser Window Object

See also:
  + [The Document Object Model (DOM)](document-object-model.md)
  + [The Document Object](document.md)

Get current browser window dimensions:

```` js
window.innerHeight
window.innerWidth
````

Get information about the URL of the current page:

```` js
window.location
window.location.href
window.location.protocol
window.location.host
window.location.port
window.location.pathName
window.location.toString()
````

### Storage

Reference: https://www.w3schools.com/html/html5_webstorage.asp.

The browser window object provides us with an ability to persist or save data for longer periods of time. In the case of "local storage", the data will persist without expiration, whereas in the case of "session storage", the data will expire when the user closes their browser tab.

We can access both the local storage and session storage as properties of the window object, or using shorthand that omits the reference to the window object:

```js
window.localStorage //> Storage {length: 0}

// alternative syntax (without window object):
localStorage //> Storage {length: 0}
```

```js
window.sessionStorage //> Storage {length: 0}

// alternative syntax (without window object):
sessionStorage //> Storage {length: 0}
```

Both these storage objects implement the same API, so we can treat them similarly, using similar methods and operations. In general, these storage objects behave similar to [objects](./datatypes/objects.md) in the sense we can set and get values by referencing the corresponding key name.

In this example, we are saving a value to a particular storage location (for example called "userId"). Once set, we can get a value by referencing its key name:

```js
localStorage.userId = "123456789"
localStorage //> Storage {userId: '123456789', length: 1}

localStorage.userId //> "123456789"
```

```js
sessionStorage.userId = "123456789"
sessionStorage //> Storage {userId: '123456789', length: 1}

sessionStorage.userId //> "123456789"
```

We can programmatically clear the particular item from storage:

```js
localStorage.removeItem("userId")
localStorage //> Storage {length: 0}
```

```js
sessionStorage.removeItem("userId")
sessionStorage //> Storage {length: 0}
```

Finally, it is possible to clear all items from storage:

```js
localStorage.clear()
```

```js
sessionStorage.clear()
```

### Prompts

See:

  + https://developer.mozilla.org/en-US/docs/Web/API/Window/prompt
  + https://www.w3schools.com/jsref/met_win_prompt.asp

We can display a pop-up text box to ask for a user input, using the window object's `prompt()` method:

```js
var name = window.prompt("Please enter your name...", "Harry Potter");

if (name != null) {
  console.log(name)
}
```

```js
// alternative syntax (without window object):
var name = prompt("Please enter your name...", "Harry Potter");

if (name != null) {
  console.log(name)
}
```

### Alerts

We can display a pop-up alert message box using the window object's `alert()` method:

```` js
window.alert("HELLO WORLD")

// alternative syntax (without window object):
alert("HELLO WORLD")
````

### Timeouts

We can invoke a [function](./functions.md) after waiting for a specified duration of time, using the window object's `setTimeout()` method:

```` js
function doStuff() {
  console.log("PATIENTLY WAITING")
}

// invoke immediately:
doStuff()

// invoke after waiting 5 seconds:
window.setTimeout(doStuff, 5000)

// alternative syntax (without window object):
setTimeout(doStuff, 5000)
````

### Intervals

We can invoke a [function](./functions.md) at specified intervals, using the window object's `setInterval()` method:

```` js
function doStuff() {
  console.log("DOING IT AND DOING IT AND DOING IT WELL")
}

// invoke once per second:
window.setInterval(doStuff, 1000)

// alternative syntax (without window object):
setInterval(doStuff, 1000)
````

To be able to programmatically also stop the intervals, we need to store the result in a variable that we later pass to the `clearInterval()` function:

```` js
function doStuff() {
  console.log("DOING IT AND DOING IT AND DOING IT WELL")
}

// invoke once per second:
var myInterval = window.setInterval(doStuff, 1000)

// stop invoking:
clearInterval(myInterval)
````
