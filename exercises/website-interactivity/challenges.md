# Interactivity Exercise Challenges

## Stocks Page

Add a new page called "stocks.html" to your "interactivity-exercise" website, and paste the following contents inside:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Stocks Page</title>
  </head>
  <body>
    <h1>My Stocks Page</h1>

    <select id="stock-selector">
      <option value="MSFT" selected=true>Microsoft</option>
      <option value="GOOG">Google</option>
      <option value="AAPL">Apple</option>
    </select>

    <p>Latest Date: <span id="latest-date">some placeholder content</span></p>
    <p>Latest Closing Price: <span id="latest-closing-price">some placeholder content</span></p>

    <script>

      // FYI: this is JavaScript
      console.log("HELLO FROM THE STOCKS PAGE!")

      // select elements from the document:
      var stockSelector = document.getElementById("stock-selector")
      var latestDateParagraph = document.getElementById("latest-date")
      var latestPriceParagraph = document.getElementById("latest-closing-price")

      var cachedResponse // response data will only be accessible within the scope of the fetch() statement, so provide a variable in the global scope we can store response data to, for debugging in the console

      // define a function with logic to request stock market data and write the results to the page:
      function updateStockData() {

        // get the selected stock from the <select> element:
        var symbol = stockSelector.value
        console.log("STOCK SYMBOL:", symbol)

        // compile the request URL
        // see: https://www.alphavantage.co/documentation/#daily
        var requestUrl = "https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&apikey=abc123&symbol=" + symbol
        console.log("REQUEST URL:", requestUrl)

        // issue the HTTP request to the specified URL
        // see: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch
        fetch(requestUrl)
          .then((response) => {
            return response.json();
          })
          .then((responseData) => {
            console.log("RESPONSE DATA:", responseData)
            cachedResponse = responseData // store the response data in a variable that can be accessed after the request has been made (so you can debug via the console)

            // determine latest date and closing price
            // depends on the specific nested structure of our responseData
            // for data structure, see: https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=MSFT&apikey=demo
            var tsd = responseData["Time Series (Daily)"]
            var daily_entries = Object.entries(tsd) // see: https://github.com/prof-rossetti/intro-to-web-dev/blob/master/notes/javascript/notes.md#object-methods
            console.log("LATEST ENTRY", daily_entries[0])
            var latestDate = daily_entries[0][0] // "2020-01-24"
            console.log("LATEST DATE:", latestDate)
            var latestClose = tsd[latestDate]["4. close"]
            console.log("LATEST CLOSING PRICE:", latestClose)

            // update page contents:
            latestDateParagraph.innerHTML = latestDate
            latestPriceParagraph.innerHTML = "$" + latestClose
          })
      }

      // update when the page loads for the first time:
      updateStockData()

      // also update when a stock is selected:
      stockSelector.addEventListener("change", updateStockData, false)

    </script>
  </body>
</html>
```

The JavaScript provided at the bottom of the page issues an HTTP request to the [AlphaVantage API](https://www.alphavantage.co/) and processes the resulting response data containing recent prices for the selected stock.

Visit your page in the browser and observe the page contents update after a request has been made for the stock's data.

## Stocks Dashboard

Leverage the capabilities of a third-party JavaScript charting library like [Highcharts.js](/notes/javascript/highcharts.md) or [Plotly.js](/notes/javascript/plotly.md) to create a line graph data visualization of the stock's daily closing prices over time.

The first step will be do create an example line graph using example data provided by the library documentation. Then the hardest step will be to transform the stock data into the data structure the chart is looking for.

![](stocks-dashboard.png)
