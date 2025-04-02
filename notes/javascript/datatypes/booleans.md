
# Booleans

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean.

In JavaScript, `true` and `false` are reserved words which indicate boolean values.

```` js
true

false
````

## Operations

The most relevant boolean operator is the equality operator (`==`), which compares the value on the left to the value on the right, essentially asking the question "Is this equal to that?":

```` js
true == true //=> true

true == false //=> true

false == false //=> false
````

The opposite of the equality operator is the inequality operator (`!=`):

```` js
true != true //=> false

true != false //=> true

false != false //=> false
````

In JavaScript, there are also "strict" versions of these operators (`===` and `!==`) that take datatypes into consideration:

```js
5 == "5" //> true

5 === "5" //> false
```


Here is more information about [Comparison Operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Comparison_operators), for your reference.
