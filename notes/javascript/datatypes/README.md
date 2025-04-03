
# JavaScript Datatypes Overview

As contrasted against [functions](../functions.md), which are like verbs within the scope of our program, objects are like the nouns.

In programming, each object belongs to a given class called a "datatype". There are a handful of different datatypes in the JavaScript language. The datatype of an object determines how the data is stored in memory, and more practically determines what operations we can perform with that object.

Here are some examples of common objects and their datatypes:

```js
// BOOLEANS:
true
false

// UNDEFINED (LIKE A NULL VALUE):
undefined

// NUMBERS:
100
0.45

// STRING (TEXTUAL MESSAGE):
"Hello World"

// DATE:
new Date(2025,4,2)

// ARRAY:
[1,2,3,4]

// OBJECT:
{title: "Harry Potter and the Deathly Hallows: Part 2", year: 2011}
```

> TERMINOLOGY NOTE: even though there is a specific datatype called the "object" datatype which we will study later, in this document we are using the term "object" to generically refer to any of these datatypes.

## Datatype Detection

In many cases, we can use the `typeof()` function to detect the datatype of a given object:

```` js
typeof(true) //> boolean
typeof(false) //> boolean

typeof(undefined) //> undefined

typeof(100) //> number
typeof(0.45) //> number

typeof("Hello World") //> string

typeof( new Date() ) //> object

typeof( {a:1, b:2} ) //> object

typeof( [1,2,3] ) //> object

typeof( function doStuff(){} ) //> function
````

However note that one of the weaknesses of the JavaScript language is that complex objects like arrays, objects, and dates don't technically have their own datatypes (they are all considered as "objects").

## Why Datatypes Matter

Knowing what datatype an object is determines what operations we can perform on it. For example, when we use the plus sign operator with a number, it performs an addition operation, whereas when we use the plus sign operator with a string, it performs a concatenation operation:

```js
console.log(2 + 2) //> 4

console.log("2" + "2") //> "22"
```

If you are not paying attention to what datatypes you're using, your program may behave in unintended ways. This is one of the reasons why datatypes are so important.

## Datatype Conversion

It is possible to convert certain types of objects from one datatype to another. Here are a few examples of datatype conversion functions:

```` js
// converting string to number (integer):
parseInt("500") //> 500

// converting string to number (float):
parseFloat("0.45") //> 0.45

// converting string to unix timestamp (which is like a numeric representation of a date):
Date.parse("March 21, 2012") //> 1332302400000

// converting number to string:
var i = 100
i.toString() //> "100"
````

Datatype conversions can help us avoid some of the issues we saw when working with mixed datatypes:

```js
console.log(2 + parseInt("2")) //> 4
```

# JavaScript Datatypes In Depth

See the subsections below for more information about each of these different datatypes:

   + [Booleans](booleans.md)
   + [Strings](strings.md)
   + [Numbers](numbers.md)
   + [Dates](dates.md)
   + [Arrays](arrays.md)
   + [Objects](objects.md)
