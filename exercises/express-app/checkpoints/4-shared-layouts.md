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

Let's create that shared layout now in a new view file called "layout.ejs":

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

## Boostrap Layout

Optionally upgrade your layout to use Bootstrap styles and navbar:

```html
```
