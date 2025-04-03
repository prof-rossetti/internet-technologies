# JavaScript Language Overview

This document contains a high level overview of the JavaScript language. For more details, see the external resources linked below.

## References

Mozilla Guides:

  + [JavaScript First Steps](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps)
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
console.log("HELLO WORLD") // THIS IS A COMMENT
````

```js
// console.log("HELLO WORLD")
```

Multi-line comments:

```` js
/*
THIS IS A MULTILINE COMMENT

console.log("HELLO WORLD")
console.log("ANOTHER MESSAGE")
*/
````

> FYI: in these tutorials, we will be using comments like `//>` to denote the outputs of certain statements.

### Logging

Output, or "log" an object to the browser's console:

```` js
console.log("HELLO WORLD") //> HELLO WORLD
````

Log multiple objects:

```` js
console.log("HELLO WORLD", 5, 9999, "GOODBYE!")  //> HELLO WORLD 5 9999 GOODBYE!
````


### Variables

Declare a variable using the syntax `var` then the name of the variable, then assign its value by using a single equal sign (`=`) followed by the value. Any datatype can be stored in a variable.

```` js
var x = 2 + 2
console.log(x)
````

> NOTE: in some of the external resources you may see sometimes we use `let` or `const` instead of `var` for variable assignment. Basically `let` allows us to lazily assign a value, and `const` is used to assign "constant" values we don't expect to change. For this course if you want to stick to using `var`, that will be fine.

Variables can be defined without yet being assigned a value. In this case, the variable's value is said to be "undefined".

```` js
var u
console.log(u) //> undefined

u = 100
console.log(u) //> 100
````


### [Datatypes](datatypes/README.md)

### [Functions](functions.md)

### [Control Flow](control-flow.md)

### [Errors](errors.md)

### [Debugging](debugging.md)
