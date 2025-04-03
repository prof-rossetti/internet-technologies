
# Errors

## Handling Errors

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch.

Sometimes errors will happen, and when they do they might cause a program to crash. However it is possible to gracefully handle errors using a "try ... catch" statement. We wrap the potentially problematic code inside the "try" block, and we specify inside the "catch" block some code that should be executed in case of an error.

````js
try {
   var x = document.oops() // INVALID CODE, THROWS AN ERROR
   console.log("TRYING TO DO STUFF HERE") // NEVER REACHED
} catch (err) {
   console.log("CAUGHT AN ERROR", err)
}
//> CAUGHT AN ERROR TypeError: document.oops is not a function
````

## Throwing Errors

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw.

It is possible to raise, or "throw" your own custom errors:

```` js
throw "MyError"
````
