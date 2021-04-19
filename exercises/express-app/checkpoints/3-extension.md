# Express App Exercise Part 3: Extension

## Index Routes

Let's create the routing and views for a few more pages (i.e. "About" and "Hello"), and include consistent navigation across all pages:

Updated "index.ejs" view:

```html
<!DOCTYPE html>
<html>
  <head>
    <title><%= title %></title>
    <link rel='stylesheet' href='/stylesheets/style.css' />
  </head>
  <body>

    <h1><%= title %></h1>
    <p>Welcome to <%= title %></p>

    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/hello">Hello</a></li>
        </ul>
    </nav>

    <footer>
        <p>My footer</p>
    </footer>

  </body>
</html>

```

New "about.ejs" view:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>About Page</title>
    <link rel='stylesheet' href='/stylesheets/style.css' />
  </head>
  <body>

    <h1>About Me</h1>
    <p>This is the about page... </p>

    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/hello">Hello</a></li>
        </ul>
    </nav>

    <footer>
        <p>My footer</p>
    </footer>

  </body>
</html>
```

New "hello.ejs" view:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello Page</title>
    <link rel='stylesheet' href='/stylesheets/style.css' />
  </head>
  <body>

    <h1><%= message %></h1>
    <p>This is the hello page... </p>

    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/hello">Hello</a></li>
        </ul>
    </nav>

    <footer>
        <p>My footer</p>
    </footer>

  </body>
</html>

```

New index routes:

```js
// this is the "routes/index.js" file...
//...

/* GET about page. */
router.get('/about', function(req, res, next) {
  res.render('about');
});

/* GET hello page. */
router.get('/hello', function(req, res, next) {
  console.log("URL PARAMS:", req.query)
  var name = req.query.name || "World" // double pipes is an OR operator that allows us to use a default value if the url params are null / not specified
  var message = "Hello, " + name
  res.render('hello', { message: message });
});

//...
```

Visit the following routes in the browser to see how everything is working:
   + http://localhost:3000/
   + http://localhost:3000/about
   + http://localhost:3000/hello
   + http://localhost:3000/hello?name=Tally
   + http://localhost:3000/hello?name=John%20Snow

Make a commit with a message like "Navigable pages".

## User Routes

Let's also add another user route to demonstrate an alternative way of handling named required URL parameters:

```js
// this is the "routes/users.js" file...
//...

router.get('/:id', function(req, res, next) {
  var userId = req.params.id;
  console.log("USER ID:", userId)

  var user = {"id": userId, "name": "Example User", "email": "example@example.com"} // just some dummy data
  res.send(user);
});

//...
```

Visit the following routes in the browser to see the server detect and handle the dynamic `:id` param:
   + http://localhost:3000/users/99
   + http://localhost:3000/users/100

Nice, we are starting to build our own custom web application, and we have learned how to handle various kinds of request parameters.

Before moving on, let's make another commit with a message like "Another user route".
