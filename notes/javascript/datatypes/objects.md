
# Objects

Reference: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object.

Example objects:

```js
{}

{"a": 1, "b": 2, "c": 3}

{"a": 1, "b": 2, "c": 3, "fruits": ["apple", "banana", "pear"]} // objects can contain lists, or even other nested objects

{"first_name": "Ophelia", "last_name": "Clark", "message": "Hello Again"}
```

Each object is similar to a row in a CSV-formatted spreadsheet or a record in a database, where the object's "keys" represent the column names and its "values" represent the cell values.

city | name | league
--- | --- | ---
New York | Yankees | major
New York | Mets | major
Boston | Red Sox | major
New Haven | Ravens | minor


```js
[
    {"city": "New York", "name": "Yankees", "league":"major"},
    {"city": "New York", "name": "Mets", "league":"major"},
    {"city": "Boston", "name": "Red Sox", "league":"major"},
    {"city": "New Haven", "name": "Ravens", "league":"minor"}
]
```


## Operations

Access individual object elements by their key:

```` js
var person = {first:"Ophelia", last:"Clarke", message:"Hello world", favoriteCities:["New York", "Denver", "San Francisco"]}

person["first"] //> "Ophelia"
person["last"] //> "Clarke"
person["message"] //> "Hello world"
person["favoriteCities"] //=> ["New York", "Denver", "San Francisco"]
person["favoriteCities"][0] //=> "Denver" (an array is still an array, even if it exists inside a JSON object!)
````

Add or remove items from an object:

```` js
var person = {first:"Ophelia", last:"Clarke", message:"Hello world", favoriteCities:["New York", "Denver", "San Francisco"]}

person["eyeColor"] = "Brown"

delete person["favoriteCities"];

person //=> {first: "Ophelia", last: "Clarke", message: "Hello world", eyeColor: "Brown"}
````

## `Object` Methods

Make use of built-in `Object` methods for easier data-processing:

```` js
var person = {first:"Ophelia", last:"Clarke", message:"Hello world", favoriteCities:["New York", "Denver", "San Francisco"]}

Object.keys(person) //> ["first", "last", "message", "favoriteCities"]

Object.values(person) //> ["Ophelia", "Clarke", "Hello world", Array[3]]

Object.entries(person) //> [Array[2], Array[2], Array[2], Array[2]]
````
