## Charts V2

**Points**

- What to do by default with long labels on the X and on the Y? 
- Show or not the legend by default based on the chart type/selected options

**1. Scatter plot**

In scatter plots, _time_ is always considered continuous

| **chart** | **x** | **y** | **supported** | **note**                             |
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

  

| **Chart**      | **x**                          | **y**                          | Supported                  |                                                                                                                                                                                            |
| -------------- | ------------------------------ | ------------------------------ | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| bar            | disc                           | - _(aggregation on_ **_x_**_)_ | ✅ (needs count on backend) | aggregation functions should be selectable: count, sum, mean etc…                                                                                                                          |
| bar (inverted) | - _(aggregation on_ **_x_**_)_ | disc                           | ✅                          | aggregation functions should be selectable: count, sum, mean etc…                                                                                                                          |
| bar            | disc                           | cont                           | ✅                          | the **y** axis can be either RAW or aggregated with a function to choose<br><br>Y Axis options: List of aggregation functions (stat summary functions) + none. Selecting none makes it raw |
| bar (inverted) | cont                           | disc                           | ✅                          | the **y** axis can be either RAW or aggregated with a function to choose                                                                                                                   |
| bar            | time                           | - _(count agg on_ **_x_**_)_   | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |
| bar (inverted) | - _(aggregation on_ **_x_**_)_ | time                           | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |
| bar            | time                           | cont                           | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |
| bar (inverted) | cont                           | time                           | ❌                          | in this case time is considered _discrete_                                                                                                                                                 |

- Count instead of top 10
- Aggregation: none or count
- Fill / Line color  
  
Primary axis: the discrete axis
Secondary axis: the continuous axis

What should be supported:
- [ ] Provide Primary only -> Use count(X) for the Y axis
- [ ] Provide X and Y -> use mean(Y) for each category
- [ ] Swapping the two variables (swaps the axes)
- [ ] Scales should adapt to the data
- [ ] Tooltip with the right information and standard style

Discuss with Evgeny if it is possible to have a full **count** aggregation instead of a **count top 10**

Next steps:
- Choose the aggregation function for the secondary axis
- Choose if data is Raw or Aggregated

**3. Line chart**  
**4. Box plot**  
**5. Pie chart**  
**6. Histogram**  
  
| **chart** | **x** | **y** | **supported** |
| --------- | ----- | ----- | ------------- |
| bar       | disc  | –     | ✅             |
| pie       | disc  | –     | ✅             |
| bar       | disc  | cont  | ❌             |
| boxplot   | disc  | cont  | ✅             |
| heatmap   | disc  | disc  | ❌             |
| heatmap   | disc  | time  | ❌             |
| boxplot   | cont  | –     | ✅             |
| histogram | cont  | –     | ✅             |
| bar       | cont  | disc  | ❌             |
| boxplot   | cont  | disc  | ✅             |
| scatter   | cont  | disc  | ❌             |
| heatmap   | cont  | cont  | ❌             |
| line      | cont  | cont  | ✅             |
| scatter   | cont  | cont  | ✅             |
| bar       | time  | –     | ✅             |
| histogram | time  | –     | ✅             |
| heatmap   | time  | disc  | ❌             |
| bar       | time  | cont  | ❌             |
| line      | time  | cont  | ✅             |
| scatter   | time  | cont  | ❌             |
