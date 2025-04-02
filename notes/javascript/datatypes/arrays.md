
# Arrays

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array.

Arrays are containers for many values. Arrays are like ordered lists. Arrays can contain zero or more values. Arrays can contain elements of any type, but as a best practice, array elements should share a datatype and structure.

Here are some example arrays:

```js
[]

[100, 75, 33]

["fun", "times", "right?"]

// arrays can contain objects:
[ {a:1, b:2}, {a:5, b:6}]

// arrays can be "nested" inside other arrays:
[ [1,2,3], [4,5,6], [7,8,9]]
```

## Accessors

Like other languages, individual array values can be accessed by their index. Array indices are zero-based, meaning the index of the first value in an array is 0.

```` js
var arr = ["a", "b", "c", "d"]

arr[0] //> "a"

arr[1] //> "b"

arr[2] //> "c"

arr[3] //> "d"

arr[4] //> undefined
````

## Operations

It is possible to get the index value of any item in the array:

````js
var arr = ["a", "b", "c", "d"]

arr.indexOf("a") //> 0

arr.indexOf("b") //> 1

arr.indexOf("c") //> 2

arr.indexOf("z") //> -1 (applies to any item not found in the array)
````

Counting the number of items in an array:

```` js
var arr = ["a", "b", "c", "d"]
arr.length //> 4
````

Checking to see if an item is in the array:

````js
var arr = ["a", "b", "c", "d"]

arr.includes("a") //> true

arr.includes("z") //> false
````

Adding an element to the end of an array:

```` js
var arr = ["a", "b", "c", "d"]

arr.push("e")

arr //> ["a", "b", "c", "d", "e"]
````

Concatenate two arrays:

```` js
var arr = ["a", "b", "c", "d"]
var arr2 = ["x", "y", "z"]

var arr3 = arr.concat(arr2)
arr3 //> "a", "b", "c", "d", "x", "y", "z"]
````

## Iteration

Arrays can be iterated, or "looped" using the `forEach()` function:

```` js
var arr = ["a", "b", "c", "d"]

// full order of parameters available:
arr.forEach(function(item, index, array) {
  console.log(item, index);
})

// usually we just reference the item itself:
arr.forEach(function(item) {
  console.log(item);
})
````

A common pattern is to loop through one array to populate the contents of another:

```` js
var arr = [1, 2, 3, 4]
var arr2 = []

arr.forEach(function(item) {
  arr2.push(item * 100)
})

arr2  //> [100, 200, 300, 400]
````

## Mapping

Arrays can be looped "in-place" using the `map()` function:

```` js
var arr = [1, 2, 3, 4]

var arr2 = arr.map(function(x){
  return x * 100
})

arr2 //> [100, 200, 300, 400]
````

> NOTE: remember to use the `return` keyword when mapping.

> Note: the `map()` function returns an array.

## Filtering

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter.

Use the `filter()` function to select a subset of items from an array - only those items matching a given condition.

```` js
var arr = [1,2,4,8,16]

arr.filter(function(i){ return i > 2}) //> [4,8,16]
````

```` js
var teams = [
  {city:"New York", name:"Yankees"},
  {city:"New York", name:"Mets"},
  {city:"Boston", name:"Red Sox"}
]

teams.filter(function(obj){ return obj["name"] == "Yankees" })
//> [{city:"New York", name:"Yankees"}]
````

> Note: the `filter()` function returns an array, even if it is empty or only contains one item.

## Finding

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find.

Use the `find()` function to select a single items from an array - only the first item matching a given condition.

```` js
var arr = [1,2,4,8,16]

arr.find(function(i){ return i > 2}) //> 4
````

```` js
var teams = [
  {city:"New York", name:"Yankees"},
  {city:"New York", name:"Mets"},
  {city:"Boston", name:"Red Sox"}
]

teams.find(function(obj){ return obj["name"] == "Yankees" })
//> {city:"New York", name:"Yankees"}
````

> Note: the `find()` function returns a single value, or undefined.

## Sorting

Reference:
  + [Sorting Arrays - Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
  + [D3 Array Sorting](https://github.com/d3/d3-array#ascending)

We invoke the `sort` method on an array to sort the values. This performs a "mutating" operations which changes the underling array in place.

```js
var numbers = [7,2,4,9,1]
numbers.sort()
numbers //> [1, 2, 4, 7, 9]
```

```js
var letters = ["j","d","p","q","x"]
letters.sort()
letters //> ["d", "j", "p", "q", "x"]
```

For simple arrays of single values, JavaScript knows how to sort them. But for more complex arrays, such as arrays of objects, we have to provide some more information about how we want to sort:

```js
var books = [
  {title:"Book B", year:1990},
  {title:"Book X", year:1957},
  {title:"Book A", year:2030}
]

// sort books by year ascending:
books.sort(function(a, b){ return a.year - b.year })

books
//> [
//>  {title:"Book X", year:1957},
//>  {title:"Book B", year:1990},
//>  {title:"Book A", year:2030}
//>]
```

When sorting complex lists, we might want to leverage the [`d3` library](../packages/d3.md#sorting) to specify the sort order.
