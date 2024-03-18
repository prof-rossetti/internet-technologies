# The `Highcharts` Library

> Highcharts makes it easy for developers to set up interactive charts in their web pages. - [Highcharts website](http://www.highcharts.com/)

Highcharts allows you to make basic charts (Highcharts), stock charts (HighStock), and maps (Highmaps). We will be focusing on basic charts.

## Reference

  + [Source Code](https://github.com/highcharts/highcharts)
  + [API Documentation](http://api.highcharts.com/highcharts)
  + [Getting-started guide](http://www.highcharts.com/docs/getting-started/installation)
  + [Demos and Examples](http://www.highcharts.com/demo)
  + [Your First Chart](http://www.highcharts.com/docs/getting-started/your-first-chart)

## Usage

Add a chart container `<div>` to your HTML page somewhere:

```html
<div id="my-chart-container"></div>
```

Then make sure you've loaded the third-party JavaScript library (Highcharts says to add this to the `<head>`):

```html
<script src="https://code.highcharts.com/highcharts.js"></script>
```

Then add JavaScript to configure and display a chart in the container:

```html
<script>
  chartOptions = {
    chart: {
      type: 'bar'
    },
    title: {
      text: 'Food Consumption'
    },
    xAxis: {
      categories: ['Apples', 'Bananas', 'Cookies']
    },
    yAxis: {
      title: {
        text: 'Type of food eaten'
      }
    },
    series: [
      {name: 'Series A', data: [0, 0, 11]},
      {name: 'Series B', data: [2, 3, 8]}
    ]
  }
  Highcharts.chart('my-chart-container', chartOptions)
</script>
```
