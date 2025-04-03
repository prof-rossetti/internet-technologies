# Functions

Functions allow us to define some logic that can be invoked or called many times.

Like in other languages, JavaScript functions must first be defined before they can be invoked (or called).

Define a function (just once):

```` js
function doStuff(){
  console.log("DOING STUFF HERE!")
}
````

Invoke the function (any number of times):

```` js
doStuff()

doStuff()

doStuff()
````

> NOTE: the trailing parentheses are important. If they are omitted, the function will not be invoked.

## Parameters

Some functions accept parameters which can be passed to the function during its invocation. A function's parameters must be configured during the function's definition.

### Single Parameter

Define a function with a parameter:

```` js
function doStuffWithParam(message){
  console.log(message)
}
````

In this case, `message` is the name of the function's parameter. Invoke it like so:

```` js
doStuffWithParam("My Message Here")
````

```` js
var x = "My Message Here"
doStuffWithParam(x)
````

### Multiple Parameters

Defining a function with multiple parameters:

```` js
function doStuffWithParams(message, firstName, lastName){
  console.log("DOING STUFF HERE!")
  console.log(message, "says", firstName, lastName)
}
````

In this case, `message`, `firstName` and `lastName` are the names of the function's parameters. Invoke it like so:

```` js
doStuffWithParams("Hello World", "Ophelia", "Clarke")
````

When your function has multiple parameters, the order matters. You need to pass in values consistent with the order the parameters were defined.


## Returns

Use the `return` keyword when you want to pass back a value to the function's caller.

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
function add(a, b) {
  return a + b;
}

add(2,6) //> 8

// ARROW STYLE APPROACH:
const add = (a, b) => a + b;

add(2, 6) //> 8
```

Here is an example of using the arrow function syntax within a mapping approach:

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


Here is an example of using arrow functions for sorting:

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
