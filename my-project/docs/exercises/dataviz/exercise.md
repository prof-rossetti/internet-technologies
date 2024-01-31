# The Dataviz Exercise

## Prerequisites

  + ["Crunch the Data" Exercise](/exercises/crunch-the-data/README.md)

## References

  + [The Plotly Package](/notes/javascript/packages/plotly.md)

## Instructions

Search the Internet for available JavaScript dataviz libraries, or use the Plotly library as recommended.

Familiarize yourself with the package's documentation, and find some example code for bar charts, line charts, pie charts, and any other kind of chart you'd like to make.

Create a new repository and download it locally. Place inside copies of following files: ["bar_charts.html"](bar_charts.html), ["line_charts.html"](line_charts.html), and ["pie_charts.html"](pie_charts.html).

Open these pages with your text editor. Notice we are referencing / importing some JavaScript functionality from Plotly (or whichever library you chose), and we have some empty containers to hold our charts.

Preview these pages in a browser. View the JavaScript console to see some data logged there.

Write additional JavaScript at the bottom of these pages to create data visualizations of the provided data. It might not be possible to do this in a single step, so you're encouraged to work on one chart at a time, using the following process:
  1. Replicate the example from the documentation.
  2. Change / update the data that gets charted (using the example data).
  3. Ideally customize the chart appearance (e.g. adding titles, axis labels, etc.).

When you're done with the three types of charts specified, optionally create new HTML files for different types of charts of interest, and explore your ability to make those charts in JavaScript as well.

Nice, now you are more familiar with making interactive charts!

## Example Data

For your visual reference, here are some copies of the data we are charting:

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

```js
var pieData = [
    {"company": "Company X", "market_share": 0.55},
    {"company": "Company Y", "market_share": 0.30},
    {"company": "Company Z", "market_share": 0.15}
]
```
