# Stocks Dashboard Challenge

## Prerequisites

  1. ["Website Interactivity" Exercise](/exercises/website-interactivity/exercise.md)
  2. ["Crunch the Data" Exercise](/exercises/crunch-the-data/README.md)
  3. ["Dataviz" Exercise](/exercises/dataviz/exercise.md)
  4. ["Fetch the Data" Exercise](/exercises/fetch-the-data/README.md)
  5. [Obtain an AlphaVantage API Key](https://www.alphavantage.co/support/#api-key) (or use one of the prof's premium keys) and consult the [API Documentation](https://www.alphavantage.co/documentation/#dailyadj)

## Prompt

You've been hired by an investment firm to make a decision support tool, an interactive financial data dashboard, to help them decide whether to buy, sell, or hold a given stock.

The dashboard should allow a user to select from a predefined list of valid stock symbols, and click a button to fetch information about that stock.

The dashboard should then display the selected stock's latest closing price, and a line chart depicting its closing prices over time.

## Requirements

After a user inputs their API Key and selects a stock and clicks the "Go" button, the dashboard should:
  1) Capture these input values
  2) Compile the right URL given the provided inputs
  3) Fetch data from that URL
  4) Crunch the data
  5) Overwrite the HTML display values (symbol, latest close)
  6) Make a dataviz of closing prices over time

## Instructions

### Setting up the Repository

Create a new repository on GitHub, then download or "clone" the repository onto your local computer, then open the repository in a text editor, create a new "index.html" file, and paste inside the [provided "index.html" starter code](index.html).

Preview this file in the browser to see the form inputs and placeholder outputs.

### Developing

Iteratively develop the contents of your "index.html" page, using JavaScript to tackle the objectives.

You may modify the page's HTML contents if necessary, although it might not be necessary.

HINT: when crunching the time series data returned by this API, it might be helpful to use [`Object` methods](/notes/javascript/datatypes/objects.md#object-methods) like `Object.keys()` and `Object.values()` to convert the nested time series object into easier-to-work-with arrays.

### Deploying

Finally, configure GitHub Pages to host your website so it is publicly-accessible over the Internet.

Note the URL of your hosted site, and use this URL for deliverable submission purposes, and for sharing with friends.
