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

Store data:

```` js
window.localStorage //> Storage {length: 0}
window.localStorage.userID = "ABCD"
window.localStorage //> Storage {userID: "ABCD", length: 1}
````

### Alerts

Display a pop-up alert message box:

```` js
window.alert("HELLO WORLD")

// alternative syntax (without window object):
alert("HELLO WORLD")
````

### Timeouts

Invoke a [function](./functions.md) after waiting for a specified duration of time:

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

Invoke a [function](./functions.md) at specified intervals:

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
