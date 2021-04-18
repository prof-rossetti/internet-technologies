# Express App Exercise Part 2: Observation

## Initialization

Let's view the "app.js" file to see how our web app is being initialized:

```js
// this is the "app.js" file...
// ...
var indexRouter = require('./routes/index');
var usersRouter = require('./routes/users');
// ...
var app = express();
// ...
app.use('/', indexRouter);
app.use('/users', usersRouter);
// ...
```

We see the new express app is using route definitions imported from the "routes/index.js" and "routes/users.js" files. Let's inspect those files to see the routing logic defined there.

## Routing and Views

### Rendering HTML Templates

When we inspect the index routes file, we see there is a function to handle requests to the "/" path, and respond by rendering an HTML template called "index".

```` js
// this is the "routes/index.js" file...

var express = require('express');
var router = express.Router();

/* GET home page. */
router.get('/', function(req, res, next) {
  res.render('index', { title: 'Express' });
});

module.exports = router;
````

We also see the route passing some data object with a `title` attribute to the HTML page. Let's examine the "views/index.ejs" file to see how it is using the data:

```` html
<!DOCTYPE html>
<html>
  <head>
    <title><%= title %></title>
    <link rel='stylesheet' href='/stylesheets/style.css' />
  </head>
  <body>
    <h1><%= title %></h1>
    <p>Welcome to <%= title %></p>
  </body>
</html>
````

Here we see some embedded JavaScript (EJS) syntax, which is not HTML or JavaScript. We see we can use a snippet like `<%= title %>` to reference the data passed from the router.

Let's modify the value of the `title` variable in the route definition, changing it from `'Express'` to something else like `'My App'`. Refresh the browser and see the updated index page contents.

Cool, we now know how to render HTML templates and pass data to them.

### Responding with JSON Data

When we inspect the user routes file, we see there is a function to handle requests to the "/" path, but since these routes have been anchored to the "users" namespace in the "app.js" file, really this route is responding to requests to "/users".

```` js
// this is the "routes/users.js" file...

var express = require('express');
var router = express.Router();

/* GET users listing. */
router.get('/', function(req, res, next) {
  res.send('respond with a resource');
});

module.exports = router;
````

Right now instead of rendering an HTML template, this route is returning some simple string data.

Let's change it to return some JSON data instead:

```` js
// this is the "routes/users.js" file...
// ...
router.get('/', function(req, res, next) {
  var users = [
    {"id": 1, "name": "Jane McConnel", "email": "jane@example.com"},
    {"id": 2, "name": "Earl Jones", "email": "earl@yahoo.com"},
    {"id": 3, "name": "Sammy Student", "email": "sammy@myschool.edu"},
  ] // just some dummy data
  res.send(users);
});
// ...
````

Nice, now when we view http://localhost:3000/users in the browser we should see the JSON data returned from the server.


Commit your project to version control. With a better understanding of how the app is working, we are now ready to extend it.
