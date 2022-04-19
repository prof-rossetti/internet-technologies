# Express App Exercise Part 5: Processing Data

In previous exercises like the "Fetch the Data" exercise, we've seen how to make requests on the client-side, but if our request requires us to pass some secret credential like an API key, it is more secure to make that request on the server-side. Doing so allows us to keep our secret credentials separate from the client-side code.

In this checkpoint we will learn how to handle form data, and respond to POST requests. We'll also send server-side requests, and pass the data back to our application's views, including to some client-side JavaScript on that page.

## Environment Variable Configuration

We're going to make requests to the [AlphaVantage API](https://www.alphavantage.co) for stock market data, so first obtain a premium AlphaVantage API Key from the professor (e.g. "abc123").

Next, create a new file in the root directory called ".env", and place the following contents inside, using your own API Key value:

```sh
# this is the ".env" file...

ALPHAVANTAGE_API_KEY="abc123"
```

Ensure the ".env" file is ignored via an entry in the ".gitignore" file (which should have happened during repo creation). This prevents our local ".env" file and its contents from being tracked in version control, and prevents our secret credentials from being uploaded to GitHub, where they would be exposed.

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

Make a commit with a message like "Setup environment variables", but before you do, make sure the ".env" is EXCLUDED from the files you commit. Otherwise, revisit your ".gitignore" file and ensure there is a line that says ".env".

## New Routing and Views

Let's make a new stocks form which will allow the user to input a stock symbol. We'll create routes to render this form and capture data sent by the form. We'll then use form data to make a server-side request to another API, and finally return data back to a new stocks dashboard page.

Add a new file in the "routes" directory called "stocks.js" and place the following contents inside:

```js
// this is the "routes/stocks.js" file...

// see: https://www.npmjs.com/package/node-fetch
import fetch from 'node-fetch';

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
        //req.flash("success", "Stock Data Request Success!")
        res.render("stocks_dashboard", {symbol: symbol, data: JSON.stringify(data), latestClose: latestClose});
      })
    .catch(function(err){
      console.log("STOCK DATA ERROR:", err)
      //req.flash("danger", "OOPS, Please check your inputs and try again.")
      res.redirect("/stocks/form")
    })
});

module.exports = router;
```

Updating the "app.js" file to recognize these routes:

```js
// the "app.js" file...

// ...

var stocksRouter = require('./routes/stocks') // around line 12

// ...

app.use('/stocks', stocksRouter) // around line 29

// ...
```

Update the "layout.ejs" file in the "views" directory to include a new nav link:

```html
<li class="nav-item">
    <a class="nav-link" href="/stocks/form">Stocks Form</a>
</li>
```

Create a new file called "stocks_form.ejs" in the "views" directory, and place the following contents inside:

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

Create a new file called "stocks_dashboard.ejs" in the "views" directory, and place the following contents inside:


```html
<h2>Stocks Dashboard (<%= symbol %>)</h2>

<p class="lead">Latest Close: $<%= latestClose %> </p>

<div id="chart-container" height="700px">
</div>

<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
<script type="text/javascript">

    console.log("STOCKS DASHBOARD...")

    // use data from the router!
    var symbol = '<%- symbol %>'
    var stockData = JSON.parse('<%- data %>')
    console.log(stockData)

    var tsd = stockData["Time Series (Daily)"]
    var dates = Object.keys(tsd)
    var dailyPrices = Object.values(tsd)
    var closingPrices = dailyPrices.map(obj => obj["5. adjusted close"])

    // see: https://plotly.com/javascript/line-charts/
    var series = {
        x: dates,
        y: closingPrices,
        mode: "lines+markers"
    }
    var data = [series]
    var layout = {
        title: "Daily Closing Prices for Stock: " + symbol,
        height: 600
    }
    Plotly.newPlot("chart-container", data, layout, {responsive: true})

</script>

```

In order to fetch data on the server-side, we're using the ["node-fetch" package](https://www.npmjs.com/package/node-fetch), so let's install that now:

```sh
npm install node-fetch@2 --save
```

Finally, restart the server as necessary, revisit the app in the browser, and submit the stocks form to see the app working, with the new stocks form and dashboard pages!

  + http://localhost:3000/stocks/form

Finally, make a commit with a message like "Setup stock routes".
