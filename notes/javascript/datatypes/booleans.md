
# Booleans

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean.

Computers operate on the basis of binary logic, where truth is the opposite of false.

One of the beautiful things about computer programming, as opposed to other disciplines, is that the truth is universal. In other words, there is no question about what is true. There is no blurring the lines or grey area or different subjective experiences. In programming, truth is objective.

In JavaScript, `true` and `false` are reserved words which indicate boolean values.

```` js
true

false
````

They are the opposite of each other.


## Operations

To exemplify the concept of universal truth, we can use the double equals operator (`==`) to check if these two values are equal to each other. This operator compares the value on the left to the value on the right, essentially asking the question "Is this equal to that?":

```` js
true == true //> true

true == false //> true

false == false //> false
````

The opposite of the equality operator is the inequality operator (`!=`):

```` js
true != true //> false

true != false //> true

false != false //> false
````

In JavaScript, there are also "strict" versions of these operators (`===` and `!==`) that take datatypes into consideration:

```js
5 == "5" //> true

5 === "5" //> false
```


Here is more information about [Comparison Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Comparison_operators), for your reference.
