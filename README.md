#ngHighcharts

ngHighcharts is a AngularJS module that exposes high charts.js as a collection of easy to use directives.

Highcharts information can be found at <http://www.highcharts.com/demo/>


##Using ngHighcharts

Add a reference to JQuery, Angular, and Highcharts (order is important)

```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
<script type="text/javascript" src="//ajax.googleapis.com/ajax/libs/angularjs/1.2.3/angular.js"></script>
<script src="//code.highcharts.com/highcharts.js"></script>
<script src="//code.highcharts.com/modules/exporting.js"></script>
```

Add a refernce to ngHighcharts.js (should occur after Angular)

```html
<script type="text/javascript" src="js/ngHighcharts.js"></script>
```

##Creating Charts

ngHighcharts exposes a service and a directive.

###highchart Service
The `highchart` service exposes a single method.

**defaultOptions()** Returns a JavaScript object representing the Highcharts default options.  Optionally use this to create advanced charts and pass to the directive.

###highchart Directive
The `highchart` directive can be called as a attribute, class, or element.

```
<highchart type="column" data="lineData" chart-title="title" chart-subtitle="subtitle" xaxis-title="x-axis-title" yaxis-title="y-axis-title"></highchart>
```

The directive takes the following attributes

Attr | Description
---- | -----------
type | Type of chart to create. See highchart's documentation.
chart-options | Optional. A custom chartOptions object, use `highchart.defaultOptions()` to generate the default object.
data | Recommended but optional. Object that contains the labels and series data used to render the chart. Assign to a `$scope` model, changes to the model will be automatically reflected in the chart. See more info below.
xaxis-title | Defaults to `''`. Title to use for the x-axis.
yaxis-title | Defaults to `''`. Title to use for the y-axis.
height | Defaults to `400`. Height of the chart. Chart expands to fill the width of it's container.
marker | Defaults to `true`. Display the plot marker.
legend | Defaults to `true`. Display the legend.
chart-title | Defaults to `''`. Title to display above the chart. Not recommended; instead use your own markup skills to create a title.
chart-subtitle | Defaults to `''`. Subtitle to display above the chart. Not recommended; instead use your own markup skills to create a title.



#### Chart `data` Object
The `data` object contains two properties.

Property | Description
-------- | -----------
labels | This object is mapped to `xAxis.categories`. See Highcharts documentation for details on `xAxis.categories`.
series | This object is mapped to `series`. See Highcharts document for details on `series`.

Example:

```
$scope.chartData = {
    labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
    series: [
        {
            name: 'Tokyo',
            data: [7.0, 6.9, 9.5, 14.5, 18.2, 21.5, 25.2, 26.5, 23.3, 18.3, 13.9, 9.6]
        },
        {
            name: 'New York',
            data: [-0.2, 0.8, 5.7, 11.3, 17.0, 22.0, 24.8, 24.1, 20.1, 14.1, 8.6, 2.5]
        },
        {
            name: 'Berlin',
            data: [-0.9, 0.6, 3.5, 8.4, 13.5, 17.0, 18.6, 17.9, 14.3, 9.0, 3.9, 1.0]
        },
        {
            name: 'London',
            data: [3.9, 4.2, 5.7, 8.5, 11.9, 15.2, 17.0, 16.6, 14.2, 10.3, 6.6, 4.8]
        }
    ]
}
```

You can update *data* programmaticly and the chart will automatically refresh.

