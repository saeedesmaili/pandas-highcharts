# pandas-highcharts #

## What is it ##

**pandas-highcharts** is a Python package which allows you to easily build [Highcharts plots](http://www.highcharts.com/ "Highcharts") with [pandas](https://github.com/pydata/pandas "pandas").[DataFrame](http://pandas.pydata.org/pandas-docs/dev/generated/pandas.DataFrame.html "DataFrame") objects.

## Motivation ##

* pandas is the best tool to handle data in Python
* pandas is able to produce matplotlib plots. They work pretty well but have two major drawbacks
    * Not very web friendly
    * Pretty ugly
* Highcharts produce nice, interactive plot in your browser and is very complete

## Features ##

* Same interface as DataFrame.plot
* Following parameters are handled
    * data
    * x
    * y
    * kind
    * figsize
    * use_index
    * title
    * grid
    * legend
    * style
    * logx
    * logy
    * loglog
    * xticks
    * yticks
    * xlim
    * ylim
    * rot
    * fontsize
    * position
    * stacked
    * sort_columns
    * secondary_y
    * mark_right
* Following parameters are not handled (yet) :
    * ax
    * ay
    * subplots
    * sharex
    * sharey
    * layout
    * colormap
    * colorbar
    * layout
    * table
    * yerr
    * xerr
    * kwds
* Static files (highcharts.js) are not embedded

## Installation ##

Install the package using pip
```shell
pip install pandas-highcharts
```

## Usage ##

Import it in your views
```python
import pandas_highcharts
df = ... # create your dataframe here
chart = pandas_highcharts.serialize(df, render_to = "my-chart")
```

In your templates
```html
<div id="my-chart"></div>
<script type="text/javascript">{{chart|safe}}</script>
```

## More examples ##

Please read the doc for [DataFrame.plot](http://pandas.pydata.org/pandas-docs/dev/generated/pandas.DataFrame.plot.html "DataFrame plot").

For example, with the following dataset:
```
                             A          B     C
ts                                             
2015-01-01 00:00:00   27451873   29956800   113
2015-01-01 01:00:00   20259882   17906600    76
2015-01-01 02:00:00   11592256   12311600    48
2015-01-01 03:00:00   11795562   11750100    50
2015-01-01 04:00:00    9396718   10203900    43
2015-01-01 05:00:00   14902826   14341100    53
```

```python
# Basic line plot
chart = pandas_highcharts.serialize(df, render_to="my-chart", title="My Chart")
# Basic column plot
chart = pandas_highcharts.serialize(df, render_to="my-chart", title="Test", kind="bar")
# Basic column plot
chart = pandas_highcharts.serialize(df, render_to="my-chart", title="Test", kind="barh")
# Plot C on secondary axis
chart = pandas_highcharts.serialize(df, render_to="my-chart", title="Test", secondary_y = ["C"])
# Plot on a 1000x700 div
chart = pandas_highcharts.serialize(df, render_to="my-chart", title="Test", figsize = (1000, 700))
```
