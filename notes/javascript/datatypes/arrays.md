
# Arrays

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array.

Arrays are containers for many values. Arrays use square brackets on the extremities. Arrays are like ordered lists, with commas separating each value. Arrays can contain zero or more values.

Here are some example arrays:

```js
[]

[100, 75, 33]

["fun", "times", "right?"]

// arrays can contain objects:
[ {a:1, b:2}, {a:5, b:6} ]

// arrays can be "nested" inside other arrays:
[ [1,2,3], [4,5,6], [7,8,9] ]
```

Arrays can contain items of any type, but as a best practice, the items should share a datatype and structure.

## Accessors

Like other languages, individual array values can be accessed by their index. Array indices are zero-based, meaning the index of the first value is 0:

```` js
var arr = ["a", "b", "c", "d"]

arr[0] //> "a"
arr[1] //> "b"
arr[2] //> "c"
arr[3] //> "d"
arr[4] //> undefined
````

Array slicing allows us to access a sequential subset of the array. We pass parameters indicating the index of the first item and the last item. With a slicing operation, the start index is inclusive, while the end index is exclusive:

```js
var arr = ["a", "b", "c", "d"]

arr.slice(0,2) //> ["a", "b"]
```

## Operations

It is possible to get the index value of any item in the array. In the event the array contains multiple instances of a given value, the index of the first matching value will be returned:


````js
var arr = ["a", "b", "c", "b", "a"]

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


One trick for dynamically accessing the last item in an array (no matter how many there are) is to leverage the length of the array and subtract one, to arrive at the index of the last item:

```js
var arr = ["a", "b", "c", "d"]

arr[arr.length - 1] //> "d"
```


Checking to see if an item is in the array, or not:

````js
var arr = ["a", "b", "c", "d"]

arr.includes("a") //> true
arr.includes("z") //> false

// using ! operator for "not", in this case "not in":
!arr.includes("a") // false
!arr.includes("z") // true
````

Adding an item to the end of an array:

```` js
var arr = ["a", "b", "c", "d"]

arr.push("e")
arr //> ["a", "b", "c", "d", "e"]
````

Concatenating two arrays:

```` js
var arr = ["a", "b", "c", "d"]
var arr2 = ["x", "y", "z"]

var arr3 = arr.concat(arr2)
arr3 //> ["a", "b", "c", "d", "x", "y", "z"]
````





## Iteration

Arrays can be iterated, or "looped" through, using the `forEach()` method, which allows us to access each item one at a time, no matter how many items there are. We can use a loop to process all items in the same way.

When we use the `forEach()` method, you'll notice we are using an unnamed [function](../functions.md) as a part of this iteration approach. Within this function, we technically have access to three parameters: the item itself, the index of the item, and the entire array.

```` js
var arr = ["a", "b", "c", "d"]

arr.forEach(function(item, index, array) {
  console.log(item, index)
})
//> a 0
//> b 1
//> c 2
//> d 3
````

However it is possible to omit some of those parameters. We usually will just reference the item itself:

```js
var arr = ["a", "b", "c", "d"]

arr.forEach(function(item) {
  console.log(item)
})
//> a
//> b
//> c
//> d
```

In these examples we have named the first parameter `item` however we can actually use whatever parameter name we want. It doesn't matter what name we choose, as long as we reference that same name within the function. For example, the following approach using the parameter name `letter` is equivalent:


```js
var arr = ["a", "b", "c", "d"]

arr.forEach(function(letter) {
  console.log(letter)
})
//> a
//> b
//> c
//> d
```



## Mapping

A common pattern is to loop through one array to populate the contents of another. This performs a "mapping" operation where we arrive at a transformed version of the original array:

```` js
var nums = [1, 2, 3, 4]
var biggerNums = []

nums.forEach(function(n) {
  biggerNums.push(n * 100)
})

biggerNums  //> [100, 200, 300, 400]
````

Arrays can be mapped "in-place" using the `map()` method, which allows us to omit pushing the new item to an empty list:

```` js
var nums = [1, 2, 3, 4]

var biggerNums = nums.map(function(n){
  return n * 100
})

biggerNums //> [100, 200, 300, 400]
````

> NOTE: remember to use the `return` keyword in your function when mapping.


## Filtering

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter.

We can extend this pattern, including an ["if" statement](../control-flow.md) inside the loop, to only collect items that meet a given condition:

```` js
var nums = [1, 2, 3, 4]
var matchingNums = []

nums.forEach(function(n) {
  if(n > 2){
    matchingNums.push(n)
  }
})

matchingNums //> [3, 4]
````

This performs what is known as a "filtering" operation, where we arrive at a subset of items in the array, retaining only the items that match the given condition.

We can use the `filter()` method to perform a filtering operation in place, without using an "if" statement:

```` js
var nums = [1, 2, 3, 4]

var matchingNums = nums.filter(function(n){
  return n > 2
})
matchingNums //> [3, 4]
````

> NOTE: remember to use the `return` keyword in your function when filtering.

```` js
var teams = [
  {city:"New York", name:"Yankees"},
  {city:"New York", name:"Mets"},
  {city:"Boston", name:"Red Sox"}
]

var matchingTeams = teams.filter(function(obj){
  return obj["name"] == "Yankees"
})
matchingTeams //> [{city:"New York", name:"Yankees"}]
````

> NOTE: the `filter()` method returns an array, even if it is empty or only contains one item.

## Finding

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find.

A "find" operation is similar to a filter operation, except instead of returning all matching values, it will only return the first matching value.

We can use the `find()` method to perform this operation:

```` js
var nums = [1, 2, 3, 4]

var matchingNum = nums.find(function(n){
  return n > 2
})
matchingNum //> 3
````

```` js
var teams = [
  {city:"New York", name:"Yankees"},
  {city:"New York", name:"Mets"},
  {city:"Boston", name:"Red Sox"}
]

var matchingTeam = teams.find(function(obj){
  return obj["name"] == "Yankees"
})
matchingTeam //> {city:"New York", name:"Yankees"}
````

> NOTE: the `find()` method returns either a single value, or `undefined`.

## Sorting

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort

We can invoke the `sort()` method on an array to sort the values. This performs a "mutating" operation which changes the underling array in place.

```js
var numbers = [7,2,4,9,1]
numbers.sort()
numbers //> [1, 2, 4, 7, 9]
```

```js
var letters = ["e", "d", "a", "c", "b"]
letters.sort()
letters //> ['a', 'b', 'c', 'd', 'e']
```

For simple arrays of single values like numbers or strings, JavaScript knows how to sort them. But for more complex arrays, such as arrays of [objects](./objects.md), we have to provide some more information about how we want to sort. For example, with the array of book objects below, we need to specify whether we want to sort them on the basis of the "title" key, or the "year" key.

When specifying our own sorting logic, we use an unnamed comparison function, which determines how the items will be sorted. The comparison function receives two parameters, by convention usually called `a` and `b`, representing two items in the array that are being compared:

```js
var books = [
  {title:"Book B", year:1990},
  {title:"Book X", year:1957},
  {title:"Book A", year:2030}
]

// sort books by year ascending:
books.sort(function(a, b){
  return a.year - b.year
})

books
//> [
//>  {title:"Book X", year:1957},
//>  {title:"Book B", year:1990},
//>  {title:"Book A", year:2030}
//>]
```

We see in this example we needed to use some subtraction logic to make this sorting operation work, but that's definitely not the most intuitive. To make sorting operations a lot easier, we might consider alternatively leveraging the [`d3` library](../packages/d3.md#sorting) to specify the sort order (ascending or descending).
