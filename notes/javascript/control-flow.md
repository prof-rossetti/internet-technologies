# Control Flow

Reference https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference#Control_flow.

## Conditionals

In JavaScript, conditionals are defined using the "if" keyword followed by a set of parentheses containing a logical expression to be evaluated, followed by curly braces which contain statements to be executed if that condition is met.

```` js
var x = 5

if (x > 2) {
  console.log("GREATER THAN TWO")
}
//> "GREATER THAN TWO"
````

```` js
var x = 5

if (x < 2) {
  console.log("LESS THAN TWO") // NEVER REACHED
}
````

An "if" statement may contain a single "else" clause, which is reached in the event none of the above conditions are met. The "else" clause always goes at the end as the last clause.

```` js
var x = 5

if (x > 2) {
  console.log("GREATER THAN TWO")
} else {
  console.log("NOPE") // NEVER REACHED
}
//> "GREATER THAN TWO"
````

````js
var x = 5

if (x < 2) {
  console.log("LESS THAN TWO") // NEVER REACHED
} else {
  console.log("NOPE")
}
//> "NOPE"
````


An "if" statement, regardless of whether or not it contains an "else" clause, can contain any number of "else if" clauses. An "else if" clause is like a combination of the "if" clause in the sense it contains some logical expression to be evaluated, and the "else" clause in the sense it is only reached if none of the preceding conditions are true.


```` js
var x = 5

if (x < 2) {
  console.log("LESS THAN TWO") // NEVER REACHED
} else if (x < 10) {
  console.log("LESS THAN TEN")
} else {
  console.log("NOPE") // NEVER REACHED
}
//> "LESS THAN TEN"
````


In the event multiple "else if" clauses evaluate to true, only the first one is reached:

```` js
var x = 5

if (x < 2) {
  console.log("LESS THAN TWO") // NEVER REACHED
} else if (x < 10) {
  console.log("LESS THAN TEN")
} else if (x > 0) {
  console.log("GREATER THAN ZERO") // NEVER REACHED
} else {
  console.log("NOPE") // NEVER REACHED
}
//> "LESS THAN TEN"
````

## Switch / Case Statements

A "switch" statement is similar to an "if" statement, but is only used to check if values are equal to each other, and it uses a more declarative syntax:

```` js
var fruit = "Banana"

switch(fruit) {
    case "Orange":
        console.log("JUICE IT") // NEVER REACHED
        break;
    case "Banana":
        console.log("PEEL IT")
        break;
    default:
        console.log("NOPE") // NEVER REACHED
}
//> "PEEL IT"
````

A switch statement uses the `default` keyword as a catch all (similar to an "else" clause) if none of the earlier conditions are met:

```` js
var fruit = "Apple"

switch(fruit) {
    case "Orange":
        console.log("JUICE IT") // NEVER REACHED
        break;
    case "Banana":
        console.log("PEEL IT")  // NEVER REACHED
        break;
    default:
        console.log("NOPE")
}
//> "NOPE"
````

## While Loops, Counters, and Accumulators

See: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while

With a "while" loop, we can execute a statement of code over and over as long as some condition is true.

It is possible to set up an infinite loop, although this will never stop and is problematic in practice (may crash your browser, so no need to try it out yourself):

```js
while (true) {
  console.log("INFINITE LOOP")
}
//> "INFINITE LOOP"
//> "INFINITE LOOP"
//> "INFINITE LOOP"
//> etc. (continuing on forever)
```

For this reason, we can use a condition to tell the loop when to stop. Often this is used in conjunction with a counter variable:

```js
var counter = 0

while(counter < 3){ // CONDITION
    console.log("-------")
    console.log(counter, "Hello")
    counter += 1 // INCREMENT THE COUNTER
    // NOTHING ELSE, START THE LOOP OVER
}

//> -------
//> 0 'Hello'
//> -------
//> 1 'Hello'
//> -------
//> 2 'Hello'
```
