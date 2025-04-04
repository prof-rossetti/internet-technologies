
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

String splitting, specifying a delimiter character to split on, results in an [array](./arrays.md) of individual values. If we split on an empty string character, it will convert the string to a list of all the individual characters:

```js
"Hello World".split("") //> ['H', 'e', 'l', 'l', 'o', ' ', 'W', 'o', 'r', 'l', 'd']

"Hello World".split(" ") //> ["Hello", "World"]

"MSFT, AAPL, GOOGL".split(", ") //> ["MSFT", "AAPL", "GOOGL"]
```

String inclusion checks if a specified substring is in the greater string (case sensitive):

````js
"Hello World".includes("Hello") //> true

"Hello World".includes("hello") //> false

"Hello World".includes("oops") //> false
````

## Accessors

Like [arrays](./arrays.md#accessors), we can access a given character in the string by its index position. In programming, indices start at zero (for the first character):

```js
var message = "Hello World"

message[0] //> "H"

message[1] //> "e"

// ...

message[10] // "d"

message[11] // undefined
```

String slicing allows us to access a sequential subset of the string based on position of the characters. We pass parameters to the `slice()` method indicating the index of the first character and the last character, respectively. With a slicing operation, the start index is inclusive, while the end index is exclusive:

```js
"Hello World".slice(0,5) //> Hello
```
