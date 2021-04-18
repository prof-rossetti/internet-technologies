# Express App Exercise Part 5: Processing Data

In previous exercises we've seen how to make requests on the client-side, but if our request requires us to pass some secret credential like an API key, it is more secure to make that request on the server-side. This allows us to keep our secret credentials separate from the client-side code.

In this checkpoint we will learn how to handle form data, and respond to POST requests. We'll also send server-side requests, and pass the data back to our application's views, including some client-side JavaScript on that page.

## Environment Variable Configuration

First, [obtain an AlphaVantage API Key](https://www.alphavantage.co/support/#api-key).

Next, create a new file in the root directory called ".env", and place the following contents inside, where `ALPHAVANTAGE_API_KEY` is your API Key:

```sh
# this is the ".env" file...

ALPHAVANTAGE_API_KEY="def456"
```

Ensure the ".env" file is ignored via an entry in the ".gitignore" file. This prevents our local ".env" file from being tracked in version control.

We'll use a [NPM package called "dotenv"](https://github.com/motdotla/dotenv#readme) to read this environment variable from the ".env" file and pass it indirectly to our application.

Install the "dotenv" package:

```sh
npm install dotenv --save
```

Finally, update the very top of the "app.js" file to configure the "dotenv" package, as instructed by the package documentation:

```js
// this is the "app.js" file...

require('dotenv').config(); // new line 1
// ...
```

## Development

Updated "layout.ejs" with new nav link:

```html
<li class="nav-item">
    <a class="nav-link" href="/stocks/form">Stocks Form</a>
</li>
```

A new "stocks_form.ejs" view file:

```html

<h2>Stocks Form</h2>

<p>Request some stock market data...</p>

<form action="/stocks/dashboard" method="POST">

    <label>Stock Symbol:</label>
    <input type="text" name="symbol" placeholder="MSFT" value="MSFT">
    <br>

    <label>Risk Tolerance:</label>
    <select name="risk_level">
        <option value="high">High</option>
        <option value="medium">Medium</option>
        <option value="low">Low</option>
    </select>
    <br>

    <button>Submit</button>
</form>
```

Registering new routes:

```js
var fetch = require('node-fetch');
var express = require('express');
var router = express.Router();

const API_KEY = process.env.ALPHAVANTAGE_API_KEY || "abc123" // obtain your own api key and set via environment variable

router.get('/form', function(req, res, next) {
  res.render("stocks_form");
});

router.post('/dashboard', function(req, res, next) {
  console.log("FORM DATA", req.body)
  var symbol = req.body.symbol || "OOPS"
  console.log("STOCK SYMBOL", symbol)

  var requestUrl = `https://www.alphavantage.co/query?function=TIME_SERIES_DAILY_ADJUSTED&symbol=${symbol}&apikey=${API_KEY}` // using string interpolation here, but you could alternatively do concatenation with + operators
  console.log("REQUEST URL", requestUrl)

  fetch(requestUrl)
    .then(function(response) {
        return response.json()
    })
    .then(function(data){
        console.log("STOCK DATA SUCCESS", Object.keys(data))
        var latestClose = Object.values(data["Time Series (Daily)"])[0]["5. adjusted close"]
        res.render("stocks_dashboard", {symbol: symbol, data: JSON.stringify(data), latestClose: latestClose});
      })
    .catch(function(err){
      console.log("STOCK DATA ERROR:", err)
      // todo: send a flash message as well
      res.redirect("/stocks/form")
    })
});

module.exports = router;
```

A new "stocks_dashboard.ejs" view file:

```html
<h2>Stocks Dashboard</h2>

<p>Symbol: <%= symbol %></p>
<p>Latest Close: <%= latestClose %> </p>

<div id="chart-container">
    TODO: make a chart!
</div>

<script type="text/javascript">

    console.log("STOCKS DASHBOARD...")

    // use data from the router!
    var stockData = '<%- JSON.stringify(data) %>'
    console.log(stockData)

    // todo: make a chart!

</script>
```

In order to fetch data from the server-side, we're using the "node-fetch" package, so let's install that now:

```sh
npm install node-fetch --save # https://www.npmjs.com/package/node-fetch
```

Finally, restart the server as necessary, revisit the app in the browser, and submit the stocks form to see the app working.
