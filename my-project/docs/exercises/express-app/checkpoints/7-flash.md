# Express App Exercise Part 7: Flash Messaging

## References

  + https://github.com/expressjs/session
  + https://github.com/escaladesports/express-flash-messages

## Instructions

Uncomment the two lines related to `flash()` in the "stocks.js" file in the "routes" directory.

In order to use these Flash messaging capabilities, we need to make use of [sessions](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage), so let's install some packages that will help us (by running these commands from the repo's root directory):

```sh
npm install express-session --save
npm install express-flash-messages --save
```

Update the contents of the "app.js" file:

```js
// the "app.js" file...

// ...

var session = require('express-session') // around line 9
var flash = require('express-flash-messages') // around line 10

// ...

var SESSION_SECRET = process.env.SESSION_SECRET || "super secret" // around line 16 (before app initialization)

// ...

// around line 30 (after cookie parser and express layouts stuff)
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

This code will make use of the flash messaging capabilities of the packages we installed, and display the messages as dismissible alerts.

Restart the server as necessary, preview the app in the browser, and fill out the stocks form to see the flash messaging capabilities.

Make a commit with a message like "Flash messages", then re-deploy to the server.
