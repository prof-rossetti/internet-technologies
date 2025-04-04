
# Strings

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String.

Strings represent textual messages. We can construct a string using single quotes on the extremities, or double quotes. If you need to use an apostrophe or single quote inside your string, for example in a contraction like "don't", prefer to use double quotes on the extremities to avoid breaking the quoting level:


```` js
'Hello World' // SINGLE QUOTES (OK)

"Hello World" // DOUBLE QUOTES (OK)

"Don't do nine to five" // RESPECTING THE QUOTING LEVEL
````



## Operations

String equality operators (case sensitive):

```` js
"Hello" == "Hello" //> true

"Hello" == "hello" //> false

"Hello" == "Goodbye" //> false
````


String case manipulation:

```` js
"Hello".toUpperCase() //> "HELLO"

"Hello".toLowerCase() //> "hello"
````

String concatenation joins two strings together:

```js
"Hello" + "World" //> "HelloWorld"

"Hello" + " " + "World" //> "Hello World"
```

String splitting, specifying a delimiter character to split on, results in an [array](./arrays.md) of individual values:

```js
"Hello World".split(" ") //> ["Hello", "World"]

"MSFT, AAPL, GOOGL".split(", ") //> ["MSFT", "AAPL", "GOOGL"]
```

String inclusion checks if a specified substring is in the greater string (case sensitive):

````js
"Hello World".includes("Hello") //> true

"Hello World".includes("hello") //> false

"Hello World".includes("oops") //> false
````

String slicing allows us to access a subset of the string. We pass parameters indicating the index of the first character and the last character. In programming, indices start at zero (for the first character). With a slicing operation, the start index is inclusive, while the end index is exclusive:

```js
"Hello World".slice(0,5) //> Hello
```
