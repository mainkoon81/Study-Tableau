# Visualization & Storytelling

### Communicating information about data visually
> Why are data visualizations more useful for delivering insight than just using summary statistics?
> How visual encodings influences the way we interpret information and in turn how well we can draw insights from the data? 
> What plot do you build in a given situation?
> How to encode our visuals to best communicate our findings? How to design components? 

__[two components]__
 - artistic: to be eyecatching (engaging)
 - scientific: to deliver the right insights (informative)
Summary statistics like the mean and standard deviation can be great for attempting to quickly understand aspects of a dataset, but they can also be misleading. 
<img src="https://user-images.githubusercontent.com/31917400/33559462-bf77609c-d904-11e7-8dbb-b60ae351e93b.jpg"  />

%Anscombe's Quartet: In the 4 datasets with X,Y pairs above, they all share the same stats, but data points are very different one another. Relying on only summarry statistics can be misleading!    

__[What to care?]__
 - Data type(continuous? discrete? ordinal? categorical?)
 - number of columns 
 - Quantitative over time: Line Chart
 - a couple, correlation-coefficient("strength + direction" of linear relationship): Scatter Plot
<img src="https://user-images.githubusercontent.com/31917400/33561533-cf9a5528-d90a-11e7-8f8d-4361b221a62f.jpg" width="350" height="130" />

 - Univariate: Histogram / Box and Whisker Plot / Stem and Leaf Plot / Normal Quantile Plot 
<img src="https://user-images.githubusercontent.com/31917400/33560553-f8cfd8b2-d907-11e7-92fe-6d7103b5426d.jpg"  />

 - Multivariate: Bar Chart(categorical bin) / Pareto Chart(ordinal bin, which has the most problem?) / Pie Chart
<img src="https://user-images.githubusercontent.com/31917400/33560699-65ceff06-d908-11e7-823c-06035aef8008.jpg" width="350" height="200" />
 
 - Categorical Intensive: 
   - Categorical vs Categorical vs Quantitative: Side-by-Side Bar Chart, Multi-Line Charts, Stacked Bar Chart 
<img src="https://user-images.githubusercontent.com/31917400/33563471-fba1d5b0-d90f-11e7-8ce0-61ac69a2d491.jpg" />

__[Design]__
Example in R 
```
install.packages('ggplot2')
library(ggplot2)

df = read.csv(..............) 
df2 = head(df, 30)

qplot(df2$Math.SAT, df2$Verbal.SAT, xlab = 'Math SAT Score', 
      ylab = 'Verbal SAT Score', main = 'Average SAT Scores By College')

qplot(df2$Math.SAT, df2$Verbal.SAT, xlab = 'Math SAT Score', 
      ylab = 'Verbal SAT Score', main = 'Average SAT Scores By College', 
      color = as.factor(df2$Public..1...Private..2.))

qplot(df2$Math.SAT, df2$Verbal.SAT, xlab = 'Math SAT Score',
      ylab = 'Verbal SAT Score', main = 'Average SAT Scores By College',
      shape = as.factor(df2$Public..1...Private..2.), color = df2$stud..fac..ratio)

ggplot(df2, aes(x=Math.SAT, y=Verbal.SAT, group=stud..fac..ratio)) +
  geom_point(aes(shape=stud..fac..ratio, color=as.factor(df2$Public..1...Private..2.))
```
__[tableau]__

 - I. Connecting to Data
 - II. Combining Data (connect data from multiple sources)
 - III. Worksheets
 - IV. Aggregations
 - V. Hierarchies (look at the data at a year, month, day, hour, or another level)
 - VI. Marks & Filters (controls the colors, shapes and other attributes of our data)
 - VII. Show Me (controls what our ending visual looks like)
 - VIII. Small Multiples & Dual Axis (to visualize data that needs to share an axis for comparison purposes)
 - IX. Groups & Sets (categorize our data within a visualization)
 - X. Calculated Fields (add calculated fields to a visualization on the fly)
 - XI. Table Calculations (perform comparisons of our data over time or between groups)

#### I. Connecting to Data
In the left sidebar you'll see the data sources you can connect to. For file sources, you can connect to an Excel file, a text file such as a CSV, or statistical files such as from SAS, SPSS, and R. If Tableau detects sub-tables, unique formatting, or some extraneous information, the **Data Interpreter** option becomes available. 

#### II. Combining Data 
Dragging multiple sheets(tables) into the top panel and get two different outcomes depending on where to drag it, a **union** or a **join**.

__Union:__ Drag the second sheet below the first sheet, we get a **union** (if we have multiple sheets with **columns in common** as the columns will match up). Unions stack the data on top of each other, the second sheet ends up being appended to the end of the first sheet.  

__Join:__ Drag the second sheet beside the first, we get a **join** (if both have columns that we can use for the common values).Joins combines data from the sheets based on common values. We can click on the join symbol to change the type of join being performed - Inner/Left/Right/Outter. 

#### III. Worksheets
There are three main products that we can create using Tableau: 1)Worksheets, 2)Dashboards, 3)Stories. Worksheets are the core of creating dashboards and stories. On the left, fields are split between "dimensions" and "measures". Categorical, qualitative, and time data are listed as "dimensions". Quantitative numerical data is listed as "measure". Tableau automatically aggregates measures, but not dimensions. Dimensions are used to group the data and set the level of granularity.  

__Plotting:__ Select 'sheet1' in the lower left corner to start visualization. Select the data you want to plot by dragging the fields to the "columns or rows shelves". Dragging dimension to "col-shelve" and measure fields to "row-shelves". It is aggregating the measure data for each dimension and summing the values. 

#### IV. Aggregations
When we create a plot, selecting X Dimension and Y Measure, Tableau is automatically aggregating X and Y over all records in the data set. To change the aggregation method, we can select Measure then Sum, Average, Median, and others. To get more points, we need to increase the **granularity**. That means we need to aggregate not over all the records, but over something like categories. For instance, we can drag Dimension to “Detail” in the Marks card. We can change the level of granularity by dragging dimensions to the boxes in the Marks card. By increasing the granularity, Tableau is aggregating the data over each Dimension now. We get sums of Measure and Measure for each one. The level of granularity is set by the total number of groups we have in our dimensions. We should be aware of how many items(groups) the selected category field has. Each dot can be in one of n-categories(and in one of other m-categories coz we can select multiple categories). Now the sums of Measure and Measure are being aggregated over groups in selected categories. 

<img src="https://user-images.githubusercontent.com/31917400/33619775-fa67efb2-d9dd-11e7-83e2-e23c03af5ebb.png" width="400" height="250" />

Aggregations assist in our ability to draw insights, but other times having a point for every row might be better.  

#### V. Hierarchies
When you drag "Datetime" variable to Columns, there is a little plus symbol on the "Datetime" field pill. Tableau automatically makes a hierarchy of time periods from "date" and "time" data fields. As we drill down, we get more fine divisions, from year, to quarter, to month, then day. Clicking on minus sign in them, it will go back up the hierarchy. We can make some column to absorb other column as a sub-category. Select both the catgory(mom) and sub-category(child), then, in the drop down for the category(mom), create hierarchy.  

<img src="https://user-images.githubusercontent.com/31917400/33630630-f9b0e8fe-d9ff-11e7-8347-15c03b04a734.jpg" width="600" height="150" />

#### VI. Marks & Filters
__Mark card:__ Often, we’ll want to include more dimensions in our graph. We can add dimensions to the plot (increasing granularity) by dragging dimensions or measures to the Marks shelf. It has options such as color, size, and shape. 
 - __Color:__ Most often we'll be encoding data with color. We simply drag the field to "Color" in the Marks card.
 
<img src="https://user-images.githubusercontent.com/31917400/33633792-e86d17f2-da09-11e7-854a-316439db3bb6.png" />

 - __Size:__ Dragging a field, either discrete or continuous, to "Size" will encode the data in the size of the markers. We'll most often use this encoding in a scatter plot. Below is a scatter plot with average quantity vs average profit for each country. I encoded the average discount using the size of the markers, it's clear that discounts are responsible for the countries with negative profits.

<img src="https://user-images.githubusercontent.com/31917400/33633961-7fcd4d42-da0a-11e7-92d8-8efa666c150d.png" width="400" height="250" />

 - __Shape:__ As with color and size, we can use the shape of the markers to encode data. We'll want to use **discrete data only** for this. Also, if we have too many categories the shapes are too difficult to identify.

<img src="https://user-images.githubusercontent.com/31917400/33634227-6bf14520-da0b-11e7-9714-02808609bad5.png" width="400" height="250" />

 - __Detail:__ The "Detail" card allows us to bring in a field without any visual encoding. This enables us to increase granularity without adding any graphical effect. The "Label" card adds in labels for all of our markers.

__Mark & Filter card:__ This way we can view only the data we are interested in. 

<img src="https://user-images.githubusercontent.com/31917400/33634715-1357dbf2-da0d-11e7-8551-7118d09c3768.jpg" />

#### VII. Show Me
The Show Me feature is a quick way to start with a basic graph which we can add to afterwards. We can find it in the top-right of the sheet. Selecting multiple fields we want simultaneously then clicking the show me graph. From there you can customize the graph. Show Me is usually a good start once you decide what you want to look at or show. Here, filters would definitely help us narrow to look at one question at a time. 

<img src="https://user-images.githubusercontent.com/31917400/33668273-33e708f4-da97-11e7-9f27-eb2f8d187029.jpg" width="500" height="200" /> 

#### VIII. Small Multiples & Dual Axis
Simply dragging multiple dimensions to the Columns and Rows shelves creates a small multiple. We saw this before when learning about hierarchies. 

<img src="https://user-images.githubusercontent.com/31917400/33672299-d19de4c8-daa1-11e7-9ef7-16882b930330.png" width="600" height="210" /> 


 














  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
