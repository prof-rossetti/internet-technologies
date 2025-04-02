
# JavaScript Datatypes

Use `typeof()` to return the type of any object:

```` js
typeof("Hello") //=> string

typeof(100) //=> number
typeof(0.45) //=> number

typeof(true) //=> boolean
typeof(false) //=> boolean

typeof(undefined) //=> undefined

typeof( {a:1, b:2} ) //=> object

typeof( [1,2,3] ) //=> object

typeof( new Date() ) //=> object

typeof( function doStuff(){} ) //=> function
````

Here are some more examples of different datatypes:

```js
var i = 10
console.log("INTEGER:", i)

var f = 0.45
console.log("FLOAT:", f)

var s = "My Message"
console.log("STRING:", s)

var d = new Date(2025,4,2)
console.log("DATE:", d)

var a = [1,2,3,4]
console.log("ARRAY:", a)

var o = {title: "Harry Potter and the Deathly Hallows: Part 2", year: 2011}
console.log("OBJECT:", o)
```

## Datatype Conversions

Here are a few examples of how to convert between datatypes:

```` js
// convert string to number:
parseInt("500")

// convert string to number:
parseFloat("0.45")

// convert string to unix timestamp:
Date.parse("March 21, 2012")

// convert number to string:
var i = 100
i.toString() //=> "100"
````

See the subsections below for more information about each of these different data types:

   + [Booleans](booleans.md)
   + [Strings](strings.md)
   + [Numbers](numbers.md)
   + [Dates](dates.md)
   + [Arrays](arrays.md)
   + [Objects](objects.md)
