# Express App Exercise Part 4: Shared Layouts

## References

  + https://ejs.co/
  + https://github.com/soarez/express-ejs-layouts
  + https://www.npmjs.com/package/express-ejs-layouts
  + https://raddy.co.uk/blog/nodejs-express-layouts-and-partials/

## Shared Layouts

By default, EJS doesn't really do shared layouts well, but we can use another third-party package called `express-ejs-layouts` to do the job. Let's install that now:

```sh
npm install express-ejs-layouts --save
```

To use this package, we'll need to configure our app to use a shared layout:

```js
// this is the "app.js" file...
// ...
var expressLayouts = require('express-ejs-layouts'); // around line 6
// ...
app.use(expressLayouts); // around line 17
//...

```

Let's create that shared layout now in a new view file called "layout.ejs", which is a default file name the package seems to recognize / expect:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>My Web App</title>
</head>
<body>

  <!-- SITE NAVIGATION -->
  <div class="container">
    <nav>
      <h1><a href="/">My Web App</a></h1>
      <ul>
          <li><a href="/about">About</a></li>
          <li><a href="/hello">Hello</a></li>
      </ul>
    </nav>
    <hr>

    <!-- PAGE CONTENTS -->
    <div id="content">
      <%- body %>
    </div>

    <!-- FOOTER -->
    <footer>
      <hr>
      &copy; Copyright 2021 [Your Name Here] |
      <a href="https://github.com/prof-rossetti/internet-technologies/">source</a>
    </footer>
  </div>

</body>
</html>
```

Notice the `<%- body %>` placeholder is where our individual pages will insert their own content. Let's update the individual views now to inherit from our shared layout.

Updated "index.ejs" file:

```html
<h1><%= title %></h1>
<p>Welcome Home</p>
```

Updated "about.ejs" file:

```html
<h1>About Me</h1>
<p>This is the about page... </p>
```

Updated "hello.ejs" file:


```html
<h1><%= message %></h1>
<p>This is the hello page... </p>

```

Restart the server if necessary and revisit all the pages in the browser to see they look the same as before. But now our front-end code is much more maintainable.

Let's make a commit before moving on.

## Bootstrap Layout

Optionally upgrade your "layout.ejs" to use Bootstrap styles and navbar:

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-eOJMYsd53ii+scO/bJGFsiCZc+5NDVN2yr8+0RDqr0Ql0h+rP48ckxlpbzKgwra6" crossorigin="anonymous">

    <title>Hello, world!</title>
</head>
<body>

    <!--
        BOOTSTRAP NAV
        https://getbootstrap.com/docs/5.0/components/navbar/
    -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
        <div class="container-fluid">
            <a class="navbar-brand" href="/">My Web App</a>

            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav ms-auto mb-2 mb-lg-0">


                    <li class="nav-item">
                        <a class="nav-link" href="/about">About</a>
                    </li>

                    <li class="nav-item">
                        <a class="nav-link" href="/hello">Hello</a>
                    </li>

                </ul>
            </div>
        </div>
    </nav>

    <div class="container" style="margin-top:2em;">

        <!--
            PAGE CONTENTS
        -->
        <div id="content">
            <%- body %>
        </div>

        <footer style="margin-top:2em; margin-bottom:2em;">
        <hr>
            &copy; Copyright 2021 [Your Name Here] |
            <a href="https://github.com/prof-rossetti/internet-technologies">source</a>

        </footer>
    </div>

    <!-- Bootstrap JS Bundle -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.0-beta3/dist/js/bootstrap.bundle.min.js" integrity="sha384-JEW9xMcG8R+pH31jmWH6WWP0WintQrMb4s7ZOdauHnUtxwoG2vI5DkLtS3qm9Ekf" crossorigin="anonymous"></script>
    <script type="text/javascript">

        console.log("Thanks for the page visit!")

    </script>
</body>
</html>
```
