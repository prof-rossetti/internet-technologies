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

You may see JavaScript statements ending with a trailing semi-colon. In some cases it is necessary to use these trailing semi-colons, but for simplicity you are generally free to omit them.

Always observe lower-case variable and function names. If your variable or function name is comprised of two words, use camel-case, not snake case or title-case.

````
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

When programming, sometimes we want to accompany our code with comments, written in normal English.

We use comments to explain the code, and provide context.

In JavaScript, we use a double backslash character (`//`) to introduce a comment.

```js
// this is a comment
```

Observe that whatever text appears to the right of the comment is not executed. But any code to the left is still executed:

```` js
console.log("HELLO WORLD") // this is a comment
````

In JavaScript, it is possible to create multi-line comments using the `/*` characters to introduce the beginning of the comment and the `*/` characters to end the comment. Everything inside, including code, will be commented out:

```` js
/*
this is a multi-line comment
when we have more to say
or want to comment-out large portions of the code

console.log("HELLO WORLD")
console.log("ANOTHER MESSAGE")
*/
````

> FYI: in these tutorials, we will be using comments like `//>` to denote the outputs of certain statements.

### Logging

We can output, or "log" an object to the browser's console (which is accessible via the browser's inspection tools):

```` js
console.log("HELLO WORLD")
//> HELLO WORLD
````

It is possible to log multiple objects by separating them with commas:

```` js
console.log("HELLO WORLD", 5, 9999, "GOODBYE!")
//> HELLO WORLD 5 9999 GOODBYE!
````


### Variables

Let’s move on to discussing variables.

We use a variable to store a value for later. And anytime we reference that variable, we access whatever value it holds at the time we reference it.

When storing objects in variables in JavaScript, we use the keyword `var` to introduce a variable declaration, followed by the name of the variable, and then we use the equals sign (`=`) as the assignment operator. Whatever is on the right of the equals sign is stored in the variable on the left:

```` js
var x = 10
console.log(x) //> 10
````

> NOTE: in some of the external resources you may see sometimes we use `let` or `const` instead of `var` for variable assignment. Basically `let` allows us to lazily assign a value, and `const` is used to assign "constant" values we don't expect to change. For this course if you want to stick to using `var`, that will be fine.

The name "variable" means that its value can change over time:

```js
var x = 10 // VARIABLE ASSIGNMENT
console.log(x) //> 10

x = 20 // VARIABLE REASSIGNMENT
console.log(x) //> 20
```

Notice we can reference the variable's previous value when assigning a new value:

```js
var x = 10 // VARIABLE ASSIGNMENT
console.log(x) //> 10

x = x + 10 // VARIABLE REASSIGNMENT WITH SELF REFERENCE
console.log(x) //> 20

x += 10 // SHORT-HAND FOR SELF REFERENCE
console.log(x) //> 30
```

Remember, whatever is on the right side of the equals sign will be evaluated first, then stored in the variable on the left.


It is possible for variables to be defined without yet being assigned a value. In this case, the variable's value is said to be "undefined" (like a null value) until we assign it a value:

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
