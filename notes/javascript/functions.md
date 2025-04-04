# Functions

Functions allow us to define some logic that can be invoked or called many times. Functions must first be defined before they can be invoked.

Defining a function (just once):

```` js
function doStuff(){
  console.log("DOING STUFF HERE!")
}
````

Invoking the function (any number of times):

```` js
doStuff()
//> DOING STUFF HERE!

doStuff()
//> DOING STUFF HERE!

doStuff()
//> DOING STUFF HERE!
````

> NOTE: the trailing parentheses are important. If they are omitted, the function will not be invoked, but rather just referenced as a variable (which is helpful in some cases, but usually not what we want to do).

## Parameters

Some functions accept parameters which can be passed to the function during its invocation. A function's parameters must be configured during the function's definition.

### Single Parameter

Define a function with a parameter:

```` js
function doStuffWithParam(message){
  console.log(message.toUpperCase())
}
````

In this case, `message` is the name of the function's parameter. We can invoke it like so:

```` js
doStuffWithParam("My Message Here")
//> "MY MESSAGE HERE"
````

```` js
var x = "My Message Here"
doStuffWithParam(x)
//> "MY MESSAGE HERE"
````

### Multiple Parameters

Defining a function with multiple parameters:

```` js
function displayHeight(feet, inches){
  console.log("THE HEIGHT IS:", feet, "FEET AND", inches, "INCHES")
}
````

In this case, `feet` and `inches` are the names of the function's parameters. Invoke it like so:

```` js
displayHeight(6, 3)
//> THE HEIGHT IS: 6 FEET AND 3 INCHES
````

When your function has multiple parameters, the order matters. You need to pass in values consistent with the order the parameters were defined.


## Returns

By default, functions can "do stuff". But they also have the ability to "return stuff".

We use the `return` keyword to pass back a value to the function's caller. This allows us to store the return value in a variable for later use.

In this example below, because we forgot to return a value, we can't make use of the calculated value later:

```` js
function calculateArea(length, height){
  length * height // OOPS WE FORGOT TO RETURN THE RESULT
}

var area = calculateArea(4, 2)
area //> undefined
````

However by remembering to define the function properly with a return value, we now get to store that calculated value in a variable for later use:

```` js
function calculateArea(length, height){
  return length * height
}

var area = calculateArea(4, 2)
area //> 8
````

# Arrow Functions

Reference: [Arrow Functions - Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions).

FYI: there is a new "arrow function" syntax, which is a short-hand way of defining JavaScript functions. This arrow function syntax uses the `=>` symbol, and omits the curly braces normally involved in function definitions.

The following approaches are equivalent for defining a function:

```js
// TRADITIONAL APPROACH:
function add(x, y) {
  return x + y
}

add(2,6) //> 8

// ARROW STYLE APPROACH:
const add = (x, y) => x + y

add(2, 6) //> 8
```

Here is an example of using the arrow function syntax for [mapping](./datatypes/arrays.md#mapping) arrays:

```js
var numbers = [1,2,3,4,5,6,7]

// TRADITIONAL APPROACH:
var bigger1 = numbers.map(function(n){
    return n * 100
})
bigger1 //> [100, 200, 300, 400, 500, 600, 700]

// ARROW STYLE APPROACH:
var bigger2 = numbers.map(n => n * 100)
bigger2 //> [100, 200, 300, 400, 500, 600, 700]
```


Here is an example of using an arrow function for [sorting](./datatypes/arrays.md#sorting) arrays:

```js
var books = [
  {title:"Book B", year:1990},
  {title:"Book X", year:1957},
  {title:"Book A", year:2030}
]

// TRADITIONAL APPROACH:
books.sort(function(a, b){ return a.year - b.year })

// ARROW STYLE APPROACH:
books.sort((a,b) => a.year - b.year)

books
//> [
//>  {title:"Book X", year:1957},
//>  {title:"Book B", year:1990},
//>  {title:"Book A", year:2030}
//>]
```
