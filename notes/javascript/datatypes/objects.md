
# Objects

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object.

Objects are containers for many values. Objects use curly braces on the extremities. Objects are comprised of "key-value" pairs, where the key is a textual attribute name that describes and identifies the corresponding value. Objects can contain zero or more key value pairs. The keys can be defined with or without surrounding quotes.

Example objects:

```js
{}

{"a": 1, "b": 2, "c": 3}

{"city": "New York", "name": "Yankees", "league":"major"}

{name: "Murphy", breed: "Lab", ageYears: 7}
```

Objects can contain arrays, or even other nested objects:

```js
{"a": 1, "b": 2, "c": 3, "fruits": ["apple", "banana", "pear"]}
```


## Accessors

To study objects, let's consider this example object:

```js
var person = {
    first: "Ophelia",
    last: "Clarke",
    favoriteCities: ["New York", "Denver", "San Francisco"]
}
```

Accessing values by their key:

```` js
person["first"] //> "Ophelia"

person["last"] //> "Clarke"

person["favoriteCities"] //> ["New York", "Denver", "San Francisco"]
````

## Operations

Adding values to an object:

```` js
person["eyeColor"] = "Brown"

person
//> {
//>    first: "Ophelia",
//>    last: "Clarke",
//>    favoriteCities: ["New York", "Denver", "San Francisco"],
//>    eyeColor: "Brown"
//> }
````

Removing values from an object:

```` js
delete person["favoriteCities"]

person //> {first: "Ophelia", last: "Clarke", eyeColor: "Brown"}
````

## `Object` Methods

The `Object` constructor has methods that might help us further process an object.

For example, we can use it to access an array of just the keys, just the values, or the key-value pairs (i.e. the "entries"):

```` js
var person = {
    first: "Ophelia",
    last: "Clarke",
    favoriteCities: ["New York", "Denver", "San Francisco"]
}
````

````js
Object.keys(person)
//> ["first", "last", "favoriteCities"]
````

````js
Object.values(person)
//> ["Ophelia", "Clarke", ["New York", "Denver", "San Francisco"]]
````

````js
Object.entries(person)
//> [
//>    ['first', 'Ophelia'],
//>    ['last', 'Clarke'],
//>    ['favoriteCities', ["New York", "Denver", "San Francisco"]]
//> ]
````
