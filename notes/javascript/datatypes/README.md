
# JavaScript Datatypes Overview

Each object belongs to a given data type. The data type of an object determines how the data is stored in memory, and more practically determines what operations we can perform with that object.

Here are some more examples of different datatypes:

```js
var i = 10
console.log("INTEGER (NUMBER):", i)

var f = 0.45
console.log("FLOAT (NUMBER):", f)

var s = "My Message"
console.log("STRING:", s)

var d = new Date(2025,4,2)
console.log("DATE:", d)

var a = [1,2,3,4]
console.log("ARRAY:", a)

var o = {title: "Harry Potter and the Deathly Hallows: Part 2", year: 2011}
console.log("OBJECT:", o)
```

## Datatype Detection

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

## Why Datatypes Matter

Knowing what datatype an object is determines what operations we can perform on it. For example, when we use the plus sign operator with a number, it performs an addition operation, whereas when we use the plus sign operator with string datatype, it performs a concatenation operation:

```js
console.log(2 + 2) //> 4

console.log("2" + "2") //> "22"
```

This is why datatypes are so important.



## Datatype Conversion

Here are a few examples of how to convert between datatypes:

```` js
// convert string to number:
parseInt("500") //> 500

// convert string to number:
parseFloat("0.45") //> 0.45

// convert string to unix timestamp:
Date.parse("March 21, 2012") //> 1332302400000

// convert number to string:
var i = 100
i.toString() //=> "100"
````

Datatype conversions can help us avoid some of the issues we saw when working with mixed datatypes:

```js
console.log(2 + parseInt("2")) //> 4
```

# JavaScript Datatypes In Depth

See the subsections below for more information about each of these different data types:

   + [Booleans](booleans.md)
   + [Strings](strings.md)
   + [Numbers](numbers.md)
   + [Dates](dates.md)
   + [Arrays](arrays.md)
   + [Objects](objects.md)
