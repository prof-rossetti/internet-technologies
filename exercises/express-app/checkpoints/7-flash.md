# Express App Exercise Part 7: Flash Messaging

## References

  + https://github.com/expressjs/session
  + https://github.com/escaladesports/express-flash-messages

## Instructions

Uncomment the two lines related to `flash()` in the "stocks.ejs" routes file.

In order to use these Flash messaging capabilities, we need to make use of sessions, so let's install some packages that will help us:

```sh
npm install express-session --save
npm install express-flash-messages --save
```

Update "app.js":

```js
// the "app.js" file...

// ...

var session = require('express-session') // around line 7
var flash = require('express-flash-messages') // around line 8

// ...

var SESSION_SECRET = process.env.SESSION_SECRET || "super secret" // around line 17 (before app initialization)

// ...
// around line 29 (after cookie parser)
app.use(session({
  cookie: { maxAge: 60000},
  secret: SESSION_SECRET,
  name: 'stocks-app-session',
  resave: true,
  saveUninitialized: true
}));
app.use(flash())

// ...

```

Add this section to the top of the body in the "layout.ejs" file, before the nav:

```html
<!--
    FLASH MESSAGES
    https://github.com/escaladesports/express-flash-messages
-->
<div class="flash-container">
    <% const messages = getMessages() %>

    <% if (messages) { %>
        <% Object.entries(messages).forEach((obj) => { %>
            <% var category = obj[0] %>
            <% var message = obj[1] %>

            <!--
                BOOTSTRAP ALERTS
                https://getbootstrap.com/docs/5.0/components/alerts/#dismissing
            -->
            <div class="alert alert-<%= category %> alert-dismissible fade show" role="alert" style="margin-bottom:0;">
                <button type="button" class="btn-close" data-bs-dismiss="alert" aria-label="Close"></button>
                <%= message %>
            </div>

        <% }) %>
    <% } %>
</div>

```

Restart the server as necessary, preview the app in the browser, and fill out the stocks form to see the flash messaging capabilities.

Make a commit with a message like "Flash messages", then re-deploy.
