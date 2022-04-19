# Express App Exercise Part 3: Extension

## Index Routes

Let's create the routing and views for a few more pages, and include consistent navigation across all pages:

Update the "index.ejs" file in the "views" directory, to include `nav` and `footer` elements:

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

Create a new file in the "views" directory called "about.ejs", and place the following contents inside:

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

Create a new file in the "views" directory called "hello.ejs", and place the following contents inside:

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

Update the "index.js" file in the "routes" directory to add new routes for those pages:


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

  // passing a variable called "message" to the page (referencing the object's key name)
  res.render('hello', {message: message});
});

//...

```

Visit the following routes in the browser to see how everything is working:
   + http://localhost:3000/
   + http://localhost:3000/about
   + http://localhost:3000/hello
   + http://localhost:3000/hello?name=Polly
   + http://localhost:3000/hello?name=John%20Snow

Nice! Let's make a quick commit with a message like "Navigable pages".

## User Routes

Before moving on, let's quickly learn an alternative way of handling required URL parameters, but this time in a JSON route.

Let's update the "users.js" file in the "routes" directory to add another user route:

```js
// this is the "routes/users.js" file...

//...

router.get('/:id', function(req, res, next) {

  var userId = req.params.id;
  console.log("USER ID:", userId)

  // just some dummy data using the id variable
  var user = {"id": userId, "name": `User ${userId}`, "email": `user${userId}@example.com`}

  res.send(user);
});

//...

```

Visit the following routes in the browser to see the server detect and handle the dynamic `:id` param:
   + http://localhost:3000/users/99
   + http://localhost:3000/users/100

Nice, we are starting to build our own custom web application, and we have learned how to handle various kinds of request parameters.

Before moving on, let's make another commit with a message like "Another user route".
