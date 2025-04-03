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
var fruit = "Apple"

if (fruit == "Orange") {
  console.log("JUICE IT") // NEVER REACHED
} else if (fruit == "Banana") {
  console.log("PEEL IT") // NEVER REACHED
} else {
  console.log("NOPE")
}
//> "NOPE"
````


In the event multiple "else if" clauses evaluate to true, only the first one is reached:

```` js
var x = 5

if (x < 2) {
  console.log("LESS THAN TWO") // NEVER REACHED
} else if (x > 2) {
  console.log("GREATER THAN TWO")
} else if (x > 0) {
  console.log("GREATER THAN ZERO") // NEVER REACHED
} else {
  console.log("NOPE") // NEVER REACHED
}
//> "GREATER THAN TWO"
````

## Switch / Case Statements

A "switch" statement is similar to an "if" statement, but is only used to check if values are equal to each other, and it uses a more declarative syntax:

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
