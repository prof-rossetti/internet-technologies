
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

See the subsections below for more information about the different data types:

   + [Booleans](booleans.md)
   + [Strings](strings.md)
   + [Numbers](numbers.md)
   + [Arrays](arrays.md)
   + [Objects](objects.md)
