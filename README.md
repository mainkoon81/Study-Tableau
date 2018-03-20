# Visualization & Storytelling (Tableau)

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

 - Scatter Example in R 
```
install.packages('ggplot2')
library(ggplot2)

df = read.csv(..............) 
df2 = head(df, 30)
ggplot(df2, aes(x=col, y=col, group=sssss)) + geom_point(aes(shape=sssss, color=as.factor(df2$col_1, df$col_2, ...))
```
__[Case Study]__

1. 














__[Tableau Guildline]__

When we use DataExtract ? (http://drawingwithnumbers.artisart.org/tde-or-live-when-to-use-tableau-data-extracts/)

How to use ? (http://onlinehelp.tableau.com/current/pro/desktop/en-us/extracting_data.html)

 - I. Connecting to Data
 - II. Combining Data (connect data from multiple sources)
 - III. Worksheets & Dashboards
 - IV. Aggregations
 - V. Hierarchies (look at the data at a year, month, day, hour, or another level)
 - VI. Marks & Filters (controls the colors, shapes and other attributes of our data)
 - VII. Show Me (controls what our ending visual looks like)
 - VIII. Small Multiples & Dual Axis (to visualize data that needs to share an axis for comparison purposes)
 - IX. Groups & Sets (categorize our data within a visualization)
 - X. Table Calculations (perform comparisons of our data over time or between groups)
 - XI. Dashboard

### I. Connecting to Data
In the left sidebar you'll see the data sources you can connect to. For file sources, you can connect to an Excel file, a text file such as a CSV, or statistical files such as from SAS, SPSS, and R. If Tableau detects sub-tables, unique formatting, or some extraneous information, the **Data Interpreter** option becomes available. 

### II. Combining Data 
Dragging multiple sheets(tables) into the top panel and get two different outcomes depending on where to drag it, a **union** or a **join**.

__Union:__ Drag the second sheet below the first sheet, we get a **union** (if we have multiple sheets with **columns in common** as the columns will match up). Unions stack the data on top of each other, the second sheet ends up being appended to the end of the first sheet.  

__Join:__ Drag the second sheet beside the first, we get a **join** (if both have columns that we can use for the common values).Joins combines data from the sheets based on common values. We can click on the join symbol to change the type of join being performed - Inner/Left/Right/Outer.
 - Why some columns have **duplicate values**?  
<img src="https://user-images.githubusercontent.com/31917400/35856591-64cecc78-0b2e-11e8-8350-26d6c8769c33.jpg" width="800" height="150" /> 

 - When do we join on **multiple columns**?
<img src="https://user-images.githubusercontent.com/31917400/35856594-67dce620-0b2e-11e8-8891-44c228241564.jpg" width="800" height="120" /> 

 - Join VS Blend: When joining multiple tables, due to the difference in their level of granularities, we lose some information('str'type...numeric values will be summed up)...A Blend will be the solution for this.     
<img src="https://user-images.githubusercontent.com/31917400/35856760-dba3c3da-0b2e-11e8-9f65-06b8861e12a8.jpg" width="580" height="150" /> 

__Blend:__ A Blend is a smart join. In general, we prepare datasets(join, union, etc) before we work for fit in our workbooks. But a blend allows us to do this on the fly in our workbooks. It experiences the granularity one by one and takes selectively. We use a blend when each datasource has different levels of granularity. 
 - Open each sheet independently as two different connections(clicking and using 'show starting page' on the top left corner). 
 - In the workbooks, we can see some 'orange chain icon' on the field from the second data source.
 - As a follow up, multiple 'Marksboxs' appear.
 - Note: A blending is always a left joining, so the dataset that is brought for starters will become the primary !  
<img src="https://user-images.githubusercontent.com/31917400/35950639-710a28b0-0c6f-11e8-8427-f73277b93064.jpg" /> 

<img src="https://user-images.githubusercontent.com/31917400/35974181-e5c8a25c-0ccf-11e8-8e3f-c4da5fe607fc.jpg" /> 

 - Blend and **Dual Axis**
<img src="https://user-images.githubusercontent.com/31917400/35975150-9a2a2970-0cd3-11e8-85c4-32b2ad93644f.jpg" /> 

 - Blend and **Calculated fields**
 - How is creating calculated fields in a Blend different to creating normal calculated fields? The data elements used have to be aggregated...
<img src="https://user-images.githubusercontent.com/31917400/35988525-93073e4e-0cf6-11e8-8e21-545f9d5658d8.jpg" /> 

### III. Worksheets & Dashboards
There are three main products that we can create using Tableau: 1)Worksheets, 2)Dashboards, 3)Stories. Worksheets are the core of creating dashboards and stories. On the left, fields are split between "dimensions" and "measures". Categorical, qualitative, and time data are listed as "dimensions". Quantitative numerical data is listed as "measure". Tableau automatically aggregates measures, but not dimensions. Dimensions are used to group the data and set the level of granularity.  

__Plotting:__ Select 'sheet1' in the lower left corner to start visualization. Select the data you want to plot by dragging the fields to the "columns or rows shelves". Dragging dimension to "column-shelve" and measure fields to "row-shelves" in general. It is aggregating the measure data for each dimension and summing the values. 
 - map
<img src="https://user-images.githubusercontent.com/31917400/35782239-0725ed64-09ed-11e8-82ef-347a1b112fe3.jpg" /> 

>Q. What if we want to look at the same time-period(year) across all worksheet? What if we need a consistency? (apply **filter** across may different worksheets)?
 - Scatter Plot
<img src="https://user-images.githubusercontent.com/31917400/35783549-12823000-0a01-11e8-8d5b-ec58c53161d5.jpg" /> 

__Dashboards - Action__
 - The interactive dashboard: connect and let different workheets communicate with each other by 2 actions ('filtering' or 'highlighting') - isolating or outstanding
<img src="https://user-images.githubusercontent.com/31917400/35821452-efe2d87e-0aa0-11e8-9358-4361c0208e8f.jpg" /> 

<img src="https://user-images.githubusercontent.com/31917400/35826725-7ff2b898-0ab1-11e8-9257-5444d3090666.jpg" /> 

 - Interactivity (***Use as filter***) 
<img src="https://user-images.githubusercontent.com/31917400/36048251-8224bc10-0dd6-11e8-9872-2d1bcd91fb91.jpg" />

__Tips__
>Q. Exporting a worksheet - `Worksheet > Export > Image >`

>Q. Working with 'Extract Data'
 - Create an 'extract' for Tableau to work from (Copy and Save some data from the original)
 - When you start working with big, dynamic dataset that often changes(constantly being updated)..just like a version control, we want to work with static file to build a visual. It's like capturing and saving.  
<img src="https://user-images.githubusercontent.com/31917400/35773041-edb09144-093e-11e8-8fe4-ffa6c7cd9fa3.jpg" width="600" height="200" /> 

### IV. Aggregations

__[1) Altering aggregation]__ 
Aggregation(for numerical) and granularity(for categorical) govern how Tableau operates. Let's get straight into it !

**Time Series**
We want to see how 'certain rate' is changing as 'period' changes. 
 - 'period': Discrete or Contiguous ?
 - 'Year/Quarter/Month/Day' --- Changing the granularity(NO.of ticks) of the timeline.  
<img src="https://user-images.githubusercontent.com/31917400/35773435-70a794b6-094a-11e8-853d-b0dec8360ce3.jpg" /> 

**A.** When we create a plot, selecting 'dimension'(categorical) and 'measure'(numerical), Tableau is automatically aggregating them over all records in the data set.
 - We can switch off 'aggregation measures' from the manu bar...it will give a scatter.   

**B.** Next, we can introduce a 'dimension' that will change the level of granularity thus affect the aggregation, dragging it into the 'Marks'box(color/size/label/detail/tooltip/shape). Of course we can introduce more 'dimension'sss to increase granularity further.    

**C.** To change the aggregation method, we can select 'measure' then Sum, Average, Median, and others. To get more points, we need to increase the **granularity**. That means we need to aggregate not over all the records, but over 'dimensions'(categories). By increasing the granularity, Tableau is aggregating the data over each dimension. 
 - We get sums of 'measure' aggregated over groups in selected categories. The level of granularity is set by the total number of groups we have in our dimensions. We should be aware of **how many groups the selected category field has**. 
<img src="https://user-images.githubusercontent.com/31917400/35777698-3d7b674c-09aa-11e8-823a-d6e0dca1699e.jpg" />

 - Aggregations assist in our ability to draw insights, but other times having a point for every row might be better.
 
 - __Highlighting__
   - 'Highlighting' interrogates one of the levels in a category more specifically. Just click the legend.  
   - 'detail' in the 'Marks'box is a dark templer. The 'dimension' on the 'detail' affects the granularity but is not represented anywhere in the chart. So if we want to highlight the 'dimension' on the 'detail', we drag the 'dimension' into 'shape' then click the legend.
 - __Area Chart__
<img src="https://user-images.githubusercontent.com/31917400/35778439-2332fdee-09b6-11e8-83fb-dacc32b67f8e.jpg" /> 

>Q. Adding **filters**: We built a chart, but there is a missing 'dimension' that need to be considered, then we put this 'dimension' into a 'filter'shelve. We can customize our filter to check and isolate the chart of a particular level of the 'dimension'. 
<img src="https://user-images.githubusercontent.com/31917400/35781017-0d572b1e-09dc-11e8-807b-153390fe86c0.jpg" /> 

>Q. Adding new **custom variable**(a column of aggregation): Let's say we have, as measures, 'Units' and 'Unit_Price'. But we need to create  'total_dollar_value'. What are you gonna do? 
 - We need to multiply 'Units' by 'Unit_Price'
   - RightClick on measures and select `Create Calculated Field` then  
<img src="https://user-images.githubusercontent.com/31917400/35745386-0cc475a0-083b-11e8-9348-fc92d836ec95.jpg" /> 

% Seemingly, Richard is not the best seller overall. Now we know who deserves the bonus. 

>Q. Adding **Color**: Discrete / Continuous
 - Discrete Coloring 
<img src="https://user-images.githubusercontent.com/31917400/35746661-7496ef88-083f-11e8-80fb-ea991702daea.jpg" /> 

 - Continuous Coloring 
<img src="https://user-images.githubusercontent.com/31917400/35747886-f2fa97ae-0843-11e8-9967-3f8d9cca6fbc.jpg" width="700" height="200" />

>Q. Adding **Labels and Formatting**
 - Adding Labels: We can type our own text like.."Sales: <SUM(total_dollar_value)>"
<img src="https://user-images.githubusercontent.com/31917400/35748792-26a6b0f8-0847-11e8-965d-74eea386fc86.jpg" width="700" height="200" />

% When some text does not appear because of its size: RightClicking -> Choose `mark label > Always Show`   
 - Formatting Labels 
<img src="https://user-images.githubusercontent.com/31917400/35749792-aaf41f64-084a-11e8-8203-4f9480e91a9a.jpg" /> 

 - Formatting Axis
<img src="https://user-images.githubusercontent.com/31917400/35754487-7c8c3146-085b-11e8-9383-b0dfc087971a.jpg" width="700" height="200" /> 

__[2) Calculated Fields]__ Add 'calculated fields' to a visualization on the fly

There will be times when we want to look at something but there isn't a specific field for it. For instance, maybe we want to know the 'profit' per item for each 'order' record. It seems pretty simple, just divide 'profit' by 'order' for each record, then aggregate it. 'clalculated fields' let us create new fields to use in our visualizations. To create a calculated field, open the menu on a field (such as 'Profit'), then Create > Calculated Field....Fields in the editor show up in brackets, like [Profit]. We can do simple arithmetic here, like adding a constant, or multiplying the field. We can also use functions such as absolute value, sine, square root, etc. Here we want to create a new field that calculates the profit per item for each record - [Profit]/[Quantity]. We also renamed the calculated field to "Profit per item". 

__[3) Parameters]__ 

>Q. How to control bin size ?
<img src="https://user-images.githubusercontent.com/31917400/36004010-6030f050-0d28-11e8-824f-ca059efb29ad.jpg" />

>Q. Bin-control with 'Parameter' 
<img src="https://user-images.githubusercontent.com/31917400/36039788-7185ef02-0dbb-11e8-8572-1b406d9895b5.jpg" />


### V. Hierarchies
When you drag "Datetime" variable to Columns, there is a little plus symbol on the "Datetime" field pill. Tableau automatically makes a hierarchy of time periods from "date" and "time" data fields. As we drill down, we get more fine divisions, from year, to quarter, to month, then day. Clicking on minus sign in them, it will go back up the hierarchy. We can make some column to absorb other column as a sub-category. Select both the catgory(mom) and sub-category(child), then, in the drop down for the category(mom), create hierarchy.  
<img src="https://user-images.githubusercontent.com/31917400/33630630-f9b0e8fe-d9ff-11e7-8347-15c03b04a734.jpg" width="600" height="150" />

### VI. Marks & Filters
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

### VII. Show Me
The Show Me feature is a quick way to start with a basic graph which we can add to afterwards. We can find it in the top-right of the sheet. Selecting multiple fields we want simultaneously then clicking the show me graph. From there you can customize the graph. Show Me is usually a good start once you decide what you want to look at or show. Here, filters would definitely help us narrow to look at one question at a time. 

<img src="https://user-images.githubusercontent.com/31917400/33668273-33e708f4-da97-11e7-9f27-eb2f8d187029.jpg" width="500" height="200" /> 

### VIII. Small Multiples & Dual Axis
__Small Multiple:__ (split) Simply dragging multiple dimensions to the Columns and Rows shelves creates a small multiple. We saw this before when learning about hierarchies. The main advantages of the Small Multiples view is to be able to see 'little ranges' of our data at a time.

<img src="https://user-images.githubusercontent.com/31917400/33672299-d19de4c8-daa1-11e7-9ef7-16882b930330.png" width="600" height="210" /> 

__Dual Axis:__ (overlap) When we drag multiple Measures to the Rows shelf, we get multiple plots. If we want them in one plot, we use dual axis.   
 
<img src="https://user-images.githubusercontent.com/31917400/33672987-85b9942e-daa3-11e7-8e62-81ce7499bad9.png" width="600" height="210" />

### IX. Groups & Sets
__Groups:__ Groups are typically created from the view by selecting multiple data points in the view. We can use it in other sheets. For instance, create a map that shows how the low quantity countries (grouped) are distributed in the world. Here we used the group we created (Low Quantity Countries) to color the map. The blue countries are the ones in the group, the ones with low average quantity.

<img src="https://user-images.githubusercontent.com/31917400/33680974-261d075e-dabb-11e7-83c5-a32b1007c182.png" />

__Sets:__ Sets are similar to groups in that we can select data points and create a set from them. However, sets can be dynamic where the members of the set will change as the underlying data changes. Groups on the other hand are static, the members will always be the members. For example, say we want to see how our poor performing products are affecting the overall profits. We can create a set from the product names or IDs which lose money, where the average profit is below zero. To create the set, open the menu for the Product Name field and choose Create > Set...Click the "Condition" tab. Then select By field: Profit Average < 0 as seen below.

<img src="https://user-images.githubusercontent.com/31917400/33681307-09ca5484-dabc-11e7-8daf-ac41e4967a76.png" width="600" height="290" />

We can use the set in plots to encode these products that are losing money. Let's look at the total profits for the different sub-categories of products. With the set you just made, you can split these bars into losses and gains. The red bars are showing how much money is lost due to the bad products. It looks like Office Supplies products are almost all winners, but Furniture is losing a lot of money.

<img src="https://user-images.githubusercontent.com/31917400/33681549-cd9233fa-dabc-11e7-87c4-7bfb8573667a.png" />



### X. Table Calculations
Table calculations can be useful for helping us to compare the data that exists in a plot to other parts of the plot. What if we want to compare the percent of profits that went into each market to the total profit. Select the drop down associated with SUM(Profit), and select ```Quick Table Calculation... > Percent of Total```. Alternatively, it could be useful to look at compounding profit. A lot of table calculations work well for line plots. Let's take a look at an example. Add the Order Date to the Columns and Sales to the Rows. Make sure the Order Date is continuous. Drill down to the Quarter level, and select ```Quick Table Calculation... > Percent Difference```. 

<img src="https://user-images.githubusercontent.com/31917400/33713970-3271b880-db45-11e7-9652-1a1349868053.png" />

In order to get a better idea of how things are moving over time, we might use a **moving average**. You can see below how this is done using the table calculations. Additionally, I broke out the Category to see how things change over time for each. This plot is great for seeing the trend of the data, and that sales are increasing, but they aren't great for seeing how sales are changing over time from one quarter to the next. Instead, the last question on the next concept requires the plot below.

<img src="https://user-images.githubusercontent.com/31917400/33714331-78fd815c-db46-11e7-842c-9b4cec9700d7.png" />

 - For example
<img src="https://user-images.githubusercontent.com/31917400/36002067-ae94062c-0d20-11e8-8f2f-00081b48d195.jpg" />
 
 
### XI. Data Preparation
 - Data Interpreter: 
   - the best format of Data for machines is where each measure and dimension has its own column. 'Pivot' works for this.
   




  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
