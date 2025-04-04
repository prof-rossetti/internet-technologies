
# Numbers

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number.

Here are some examples of numbers:

```` js
100

-100

0.45
````

## Operations

When dealing with numbers we will most commonly perform arithmetic operations, which you are probably already familiar with:

```` js
100 + 5

100 - 5

100 * 5

100 / 5
````

As usual, we can use parentheses to indicate order of operations:

```` js
3 + 1 * 2 //> 5

(3 + 1) * 2 //> 8
````

Numbers also support equality operators:

```` js
100 == 100 //> true

100 == 100.0 //> true

100 == 99 //> false

100 == (99 + 1) //> true
````

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Arithmetic_operators for more information about arithmetic operators.

## `Math` Methods

For additional operations, we can use functionality provided by the "Math" object: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math.

Constants like "pi":

```` js
Math.PI //> 3.141592653589793
````

Generating a random number:

```` js
Math.random()
````

Rounding, flooring, and ceiling:

```` js
Math.round(4.555) //> 5

Math.ceil(4.555) //> 5

Math.floor(4.555) //> 4
````

Minimum and maximum values:

```` js
Math.min(4,3,7,9) //> 3

Math.max(4,3,7,9) //> 9
````
