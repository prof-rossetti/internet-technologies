
# Errors

## Handling Errors

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch.

Handle, or "catch" errors:

```` js
try {
   console.log("TRYING TO DO STUFF HERE")
} catch (err) {
   console.log(err)
}

try {
   throw("OOPS")
   console.log("TRYING TO DO STUFF HERE")
} catch (err) {
   console.log(err)
}
````

## Throwing Errors

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw.

Raise, or "throw" errors yourself:

```` js
throw "MyError"
throw 4
throw true
````
