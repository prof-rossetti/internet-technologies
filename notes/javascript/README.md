# JavaScript Language Overview

This document contains a high level overview of the JavaScript language. For more details, see the external resources linked below.

## References

Mozilla Guides:

  + [JavaScript First Steps](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps)
  + [JavaScript Basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/JavaScript_basics)
  + [JavaScript Reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference)
  + [JavaScript Statements](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements)

W3Schools Guides:

  + [Intro to JavaScript](https://www.w3schools.com/js/js_intro.asp)
  + [Where to put JavaScript](https://www.w3schools.com/js/js_whereto.asp)
  + [Logging and Output](https://www.w3schools.com/js/js_output.asp)
  + [Variables](https://www.w3schools.com/js/js_variables.asp)
  + [Functions](https://www.w3schools.com/js/js_functions.asp)

## Notes

### Syntax and Style

You may see JavaScript statements ended with a trailing semi-colon. In some cases it is necessary to use these trailing semi-colons, but you are generally free to omit them.

Always observe lower-case variable and function names. If your variable or function name is comprised of two words, use camel-case, not snake case or title-case.

```` js
// DO:
name
firstName
lastName
firstAndLastName

// DON'T:
Name
first_name
LastName
first_and_last_name
````

### Comments

Reference https://www.w3schools.com/js/js_comments.asp.

Single-line comments:

```` js
console.log("HELLO WORLD") // single-line comment
// console.log("HELLO WORLD - THIS MESSAGE IS PREVENTED FROM BEING EXECUTED")
````

Multi-line comments:

```` js
/*

multi-line comment

console.log("HELLO WORLD - THIS MESSAGE IS PREVENTED FROM BEING EXECUTED")

*/
````













### Logging

Output, or "log" an object to the browser's console:

```` js
console.log("HELLO WORLD") //> HELLO WORLD
````

Log multiple objects:

```` js
console.log("HELLO WORLD", 5, 9999, "GOODBYE!")  //> HELLO WORLD 5 9999 GOODBYE!
````

### Debugging

Insert a `debugger` statement to drop a break-point in script execution. When the break-point is reached, it will stop and allow you to interact with the state of the code at that particular line.

```` js
debugger;
````

For example:

```` js
function debugStuff(){
  console.log("START OF FUNCTION");
  var x = 100;
  debugger;
  var y = 999;
  console.log("END OF FUNCTION");
}

debugStuff()
x //=> 100
y //=> undefined
````


> Feel free to come back to this `debugger`  example after you have familiarized yourself with functions, below.


### Variables

Declare a variable using the syntax `var` then the name of the variable, then assign its value by using a single equal sign (`=`) followed by the value. Any datatype can be stored in a variable.

```` js
var i = 10
var f = 0.45
var s = "My Message"
var d = new Date(2017,02,23)
var a = [1,2,3,4]
var o = {}
var f = function(){ console.log("LOGGING FROM INSIDE A FUNCTION") }

// REFRESHER ON FUNCTION INVOCATION:
f // references the function as a variable, but does not invoke it
f() // invokes the function
````

> NOTE: when assigning a value, use a single equal sign (`=`).

Variables can be defined without yet being assigned a value. In this case, the variable's value is said to be "undefined".

```` js
var g;
g //=> undefined
g = 100
g //=> 100
````

### [Datatypes](datatypes/README.md)

### [Functions](functions.md)

### [Control Flow](functions.md)

### [Errors](errors.md)
