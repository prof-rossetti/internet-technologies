# The `Plotly` Library

## Reference

  + [Source Code](https://github.com/plotly/plotly.js/)
  + [Documentation](https://plot.ly/javascript/)
  + [Cheat Sheet](https://images.plot.ly/plotly-documentation/images/plotly_js_cheat_sheet.pdf)
  + [Responsive / Fluid Layout](https://plot.ly/javascript/responsive-fluid-layout/)
  + [Line Charts](https://plot.ly/javascript/line-charts/)
  + [Bar Charts](https://plot.ly/javascript/bar-charts/)
  + [Pie Charts](https://plot.ly/javascript/pie-charts/)

## Usage

Add a chart container `<div>` to your HTML page somewhere:

```html
<div id="my-chart-container"></div>
```

Then make sure you've loaded the third-party JavaScript library:

```html
<script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
```

Then add JavaScript to configure and display a chart in the container:

```html
<script>
  var series1 = {
    x: [1, 2, 3, 4],
    y: [10, 15, 13, 17],
    mode: "markers"
  }

  var series2 = {
    x: [2, 3, 4, 5],
    y: [16, 5, 11, 9],
    mode: "lines"
  }

  var series3 = {
    x: [1, 2, 3, 4],
    y: [12, 9, 15, 12],
    mode: "lines+markers"
  }

  var data = [ series1, series2, series3 ]

  var layout = {
    title: "Line and Scatter Plot"
  }

  Plotly.newPlot("my-chart-container", data, layout, {responsive: true})

<script>
```

The hardest part of displaying any dataviz is getting the raw data into a structure the chart wants. For this reason, the professor recommends always making example charts with static "dummy" data (like the example above) first, so you can learn what data format the chart wants. Then as a second step, transform your raw data as necessary to conform to the desired structure.
