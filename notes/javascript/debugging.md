
# Debugging

Code defined inside of a function will only be reached once the function is invoked, and we may not be as easily able to troubleshoot that code from the JavaScript console.

For example, variables defined within the scope of a function won't be available for reference outside the function:

```js
function doStuff(){
  var x = 100;
  var y = 200;
  console.log(x+y)
}

doStuff()
//> 300
```

```js
x //> undefined

y //> undefined
```

In practice, we might add `console.log` statements into the function to display the values of variables we want to troubleshoot along the way.

However there is another more robust way of debugging your code. We can insert a `debugger` statement to drop a break-point in script execution. When the break-point is reached, it will stop and allow you to interact with the state of the code at that particular line.

```` js
debugger;
````

Here is an example of using a `debugger` statement inside of a function:

```` js
function doStuff(){
  var x = 100;
  debugger;
  var y = 200;
  console.log(x+y)
}
````

With this example, when we invoke the function, it executes all the logic inside in order until it reaches the `debugger` statement, at which point it allows us to inspect the results. At this point, if we ask for the value of `x`, that has already been defined before the `debugger` statement, so we can reference that variable to learn more about it. But if we ask for the value of `y` which has not yet been reached, we see that is currently undefined.


````js
doStuff()

x //> 100

y //> undefined
````

Remember to remove or comment out any `debugger` statements after you are done troubleshooting.
