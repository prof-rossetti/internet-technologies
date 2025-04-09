
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

To calculate exponents, we can use a double asterisk as the operator:

```js
// square (raise to the power of 2):
5 ** 2 //> 25
```

As usual, we can use parentheses to indicate order of operations:

```` js
3 + 1 * 2 //> 5

(3 + 1) * 2 //> 8
````

Numbers support equality operators:

```` js
100 == 100 //> true

100 == 100.0 //> true

100 == 99 //> false
````

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Arithmetic_operators for more information about arithmetic operators.

We can round a number to a given number of decimal places by invoking the `toFixed()` method on the number, passing the number of decimal places as a parameter input. NOTE: this will return a [string](./strings.md):


```js
4.55555.toFixed(2) //> '4.56'
```

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

Rounding, flooring, and ceiling to the nearest whole number:

```` js
Math.round(4.55555) //> 5

Math.ceil(4.55555) //> 5

Math.floor(4.55555) //> 4
````

Minimum and maximum values:

```` js
Math.min(4,3,7,9) //> 3

Math.max(4,3,7,9) //> 9
````
