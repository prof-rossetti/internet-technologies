
# Debugging

Insert a `debugger` statement to drop a break-point in script execution. When the break-point is reached, it will stop and allow you to interact with the state of the code at that particular line.

```` js
debugger;
````

For example:

```` js
function debugStuff(){
  console.log("START OF FUNCTION");
  var x = 100;
  debugger;
  var y = 999;
  console.log("END OF FUNCTION");
}

debugStuff()
x //=> 100
y //=> undefined
````
