# Visualization & Storytelling

### [Contents] 

__Intro__ Communicating information about data visually

__Part-01.__ Exploring Weather Trends
  - language: R
  - func:

__Part-02.__ Visualizing Movie Data
  - language: Tableau
  - func: 

----------------------------------------------------------------------
### Intro
> Why are data visualizations more useful for delivering insight than just using summary statistics?
> How visual encodings influences the way we interpret information and in turn how well we can draw insights from the data? 
> What plot do you build in a given situation?

__[two components]__
 - artistic: to be eyecatching (engaging)
 - scientific: to deliver the right insights (informative)
Summary statistics like the mean and standard deviation can be great for attempting to quickly understand aspects of a dataset, but they can also be misleading. 
<img src="https://user-images.githubusercontent.com/31917400/33559462-bf77609c-d904-11e7-8dbb-b60ae351e93b.jpg"  />

%Anscombe's Quartet: In the 4 datasets with X,Y paairs above, they all share the same stats, buit data points are very different one another. Relying on only summarry statistics can be misleading!    

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


 














----------------------------------------------------------------------
#### >Part-01. Exploring Weather Trends

__Data:__ The Data were collected recording votes in the Irish parliament (D´ailEireann), prior to the general election, in early 2016. Extra details of the votes can be found at (http://www.oireachtas.ie/parliament/) and the data are for the votes on January 14th-28th.
There are three tables in the database:
	city_list :  This contains a list of cities and countries in the database. 
	city_data :  This contains the average temperatures for each city by year (ºC).
	global_data :  This contains the average global temperatures by year (ºC).

__Story:__ Global temperature has been a hot topic in recent years as politicians argue over climate policy. Temperature data around the world is an important part of this conversation. To measure temperature data, scientists combine measurements from the air and ocean surface. This data is collected by weather stations on land and in the ocean. I want to analyze LOCAL and GLOBAL temperature data to compare 'the temperature trends where I live' TO 'overall global temperature trends'. This project requires the following steps:
  -	Extract data from a database using a SQL query
  -	Calculate a moving average in a spreadsheet
  -	Create a line chart in a spreadsheet
  > __“Moving averages”__ are used to smooth out data to make it easier to observe long term trends and not get lost in daily fluctuations. For example, let's say we wanted to visualize the sales trend at a clothing retail store. We start with daily data, and our chart looks too volatile to interpret because more people shop on the weekends, so sales spike on those days. We could sum up sales by week, but that may take out some of the detail we wanted to see. Using a “moving average”, we can both smooth out the daily volatility and observe the long term trend. So how to calculate a moving average? 
Let’s say the dataset contains ‘daily sales data’ from 01-01-2009 to 03-31-2009. To start, create a new column called “7-day MA”, which is where the moving average field will be stored. Then, calculate the average sales for the first 7 days of sales, then next 7 days, next 7 days, and so on. 7 days’ MA, 12 days’ MA, who cares? 

__Investigation:__ Is your city hotter or cooler on average compared to the global average? Has the difference been consistent over time? How do the changes in your city’s temperatures over time compare to the changes in the global average? What does the overall trend look like? Is the world getting hotter or cooler? Has the trend been consistent over the last few hundred years?








----------------------------------------------------------------------
#### >Part-02. Visualizing Movie Data

__Data:__ The Data were collected recording votes in the Irish parliament (D´ailEireann), prior to the general election, in early 2016. Extra details of the votes can 
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
