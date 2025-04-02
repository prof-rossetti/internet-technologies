# Dates


We can construct new date objects by passing in the specified year, month, day, etc.

```js
var d = new Date(2025,4,2)
console.log(d)
```

By default if we omit passing any parameters we will get the current date and time:

```js
var now = new Date()
console.log(now)
```

## Date Formatting

The date object has various formatting methods that will help us display it in various ways:

```js
var d = new Date(2025,4,2)

console.log(d)
//> Fri May 02 2025 00:00:00 GMT-0400 (Eastern Daylight Time)

console.log(d.toDateString())
//> Fri May 02 2025

console.log(d.toLocaleDateString())
//> 5/2/2025

console.log(d.toISOString().slice(0, 10))
//> 2025-05-02
```
