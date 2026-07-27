## Charts V2

**Points**

- Axis
	- What to do by default with long labels on the X and on the Y? 
	- Dates: What to show by default? use default renderer from echarts (used for box plot) or show ISO (used for bar charts)
- Boxplot: show outlyers
- Show or not the legend by default based on the chart type/selected options
- Give a way to the user to reset the axis names if changed

**1. Scatter plot**

In scatter plots, _time_ is always considered continuous

| chart     |  x    |   y   |  supported    |  note                                |
| --------- | ----- | ----- | ------------- | ------------------------------------ |
| scatter   | cont  | disc  | ❌             | consider using _jitter_              |
| scatter   | disc  | cont  | ❌             | consider using _jitter_              |
| scatter   | cont  | cont  | ✅             |                                      |
| scatter   | time  | cont  | ❌             |                                      |
| scatter   | cont  | time  | ❌             | doable but not supported in esquisse |

**2. Bar chart  (vertical / horizontal)**

1. If discrete on the x and cont on the y, and many y values exist for the same x, if no aggregation are selected (raw data) should we group the bars like so?  
   <img width="675" height="480" alt="big krit" src="https://github.com/user-attachments/assets/f9cd4db4-d3ea-4e9f-a568-19ae3142c3e5" />

2. In bar charts, _time_ is always considered discrete
3. Scales should adapt to the data

Next steps
- Choose the aggregation function for the secondary axis
- When x and y are provided: select the sub-aggregation or select none
- Fill color: stacked

| chart          | x                              | y                              | supported                  |                                                                                                                                                                                            |
| -------------- | ------------------------------ | ------------------------------ | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| bar            | disc                           | - _(aggregation on_ **_x_**_)_ | ✅ (needs count on backend) | aggregation functions should be selectable: count, sum, mean etc…                                                                                                                          |
| bar (inverted) | - _(aggregation on_ **_x_**_)_ | disc                           | ✅                          | aggregation functions should be selectable: count, sum, mean etc…                                                                                                                          |
| bar            | disc                           | cont                           | ✅                          | the **y** axis can be either RAW or aggregated with a function to choose<br><br>Y Axis options: List of aggregation functions (stat summary functions) + none. Selecting none makes it raw |
| bar (inverted) | cont                           | disc                           | ✅                          | the **y** axis can be either RAW or aggregated with a function to choose                                                                                                                   |
| bar            | time                           | - _(count agg on_ **_x_**_)_   | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |
| bar (inverted) | - _(aggregation on_ **_x_**_)_ | time                           | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |
| bar            | time                           | cont                           | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |
| bar (inverted) | cont                           | time                           | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |

**3. Line chart**  
**4. Box plot**  
**5. Pie chart**  
**6. Histogram**  


###### Supported charts

| **chart** | **x** | **y** | **supported** |
| --------- | ----- | ----- | ------------- |
| heatmap   | disc  | disc  | ❌             |
| scatter   | disc  | cont  | ❌             |
| bar       | disc  | cont  | ✅             |
| boxplot   | disc  | cont  | ✅             |
| heatmap   | disc  | time  | ❌             |
| bar       | disc  | –     | ✅             |
| pie       | disc  | –     | ✅             |
| scatter   | cont  | disc  | ❌             |
| bar       | cont  | disc  | ✅             |
| boxplot   | cont  | disc  | ✅             |
| scatter   | cont  | cont  | ✅             |
| line      | cont  | cont  | ✅             |
| heatmap   | cont  | cont  | ❌             |
| scatter   | cont  | time  | ❌             |
| bar       | cont  | time  | ✅             |
| boxplot   | cont  | –     | ✅             |
| histogram | cont  | –     | ✅             |
| heatmap   | time  | disc  | ❌             |
| scatter   | time  | cont  | ❌             |
| bar       | time  | cont  | ✅             |
| line      | time  | cont  | ✅             |
| bar       | time  | –     | ❌             |
| histogram | time  | –     | ✅             |
| bar       | –     | disc  | ✅             |
| bar       | –     | time  | ✅             |
