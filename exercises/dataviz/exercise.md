# The Dataviz Exercise

## Prerequisites

  + ["Crunch the Data" Exercise](/exercises/crunch-the-data/README.md)

## References

  + [The Plotly Package](/notes/javascript/packages/plotly.md)

## Instructions

Search the Internet for available JavaScript dataviz libraries, or use the Plotly library as recommended.

Familiarize yourself with the package's documentation, and find some example code for bar charts, line charts, pie charts, and any other kind of chart you'd like to make.

Create a new local HTML file called "dataviz.html", with the following contents inside:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Dataviz Exercise</title>
</head>
<body>

    <h1>Dataviz Exercise</h1>

    <h2>Bar Chart</h2>
    <div id="bar-chart-container"></div>
    <br>

    <h2>Line Chart</h2>
    <div id="line-chart-container"></div>
    <br>

    <h2>Pie Chart</h2>
    <div id="pie-chart-container"></div>
    <br>

    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
    <script type="text/javascript">

        console.log("MAKING SOME CHARTS...")


        // TODO: write some JavaScript here!

    </script>
</body>
</html>

```

Open this HTML file in the text editor and preview it in the browser.

Notice we are importing some JavaScript functionality from Plotly (or whichever library you chose), and we have some empty containers to hold our charts.

Write additional JavaScript at the bottom of the page to create some example charts. Work on one chart at a time, using the following process:
  1. Replicate the example from the documentation.
  2. Change / update the data that gets charted (using the example data below).
  3. Customize the chart appearance (e.g. adding titles, axis labels, etc.).

When you're done with the three types of charts specified, optionally create new HTML markup for different types of charts of interest, and repeat the process to make those charts in JavaScript.

Nice, now you are more familiar with making interactive charts!

## Example Data

Make a bar chart from this data:

```js
var barData = [
    {"genre": "Thriller", "viewers": 123456},
    {"genre": "Mystery", "viewers": 234567},
    {"genre": "Sci-Fi", "viewers": 987654},
    {"genre": "Fantasy", "viewers": 876543},
    {"genre": "Documentary", "viewers": 283105},
    {"genre": "Action", "viewers": 544099},
    {"genre": "Romantic Comedy", "viewers": 121212}
]
```

Make a line chart from this data:

```js
var lineData = [
    {"date": "2019-01-01", "stock_price_usd": 100.00},
    {"date": "2019-01-02", "stock_price_usd": 101.01},
    {"date": "2019-01-03", "stock_price_usd": 120.20},
    {"date": "2019-01-04", "stock_price_usd": 107.07},
    {"date": "2019-01-05", "stock_price_usd": 142.42},
    {"date": "2019-01-06", "stock_price_usd": 135.35},
    {"date": "2019-01-07", "stock_price_usd": 160.60},
    {"date": "2019-01-08", "stock_price_usd": 162.62},
]
```

Make a pie chart from this data:

```js
var pieData = [
    {"company": "Company X", "market_share": 0.55},
    {"company": "Company Y", "market_share": 0.30},
    {"company": "Company Z", "market_share": 0.15}
]
```
