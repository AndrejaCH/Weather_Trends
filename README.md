# Project Overview
In this project I am analyzing and observing global weather data (temperatures) and data in selected cities (Ljubljana and Helsinki) from years 1849 to 2013. Data was retrieved from a Udacity database, using SQL queries and stored locally in csv files. In order to observe long term trends, I calculated 5-year moving averages for all datasets.

# Data Analysis Process
## Questions
-	Is local city hotter or cooler on average compared to the global average? 
-	Has the difference been consistent over time?
-	How do the changes in local city’s temperatures over time compare to the changes in the global average?
-	What does the overall trend look like? 
-	Is the world getting hotter or cooler? 
-	What is the correlation coefficient?

## Data Wrangling 
Below are listed steps in data analysis wrangling process.
Retrieving data form database using SQL queries and exporting data to csv file.

Select the city list | select data for specific cities | select all data form global_data
:---: | :---: | :---:
SELECT * FROM city_list | SELECT * FROM city_data WHERE city = 'Ljubljana'; | SELECT * FROM global_data

### Data Wrangling in Excel 
1.	Exported data from csv files to xlsx files, using copy-sheet to new file, in order to perform calculations and creating visuals.
2.	Used `VLOOKUP` formula to gather data on the same worksheet.
3.	Used `IFERROR` formula to handle missing values, replacing them with string “NULL” to avoid overwriting zeros.
4.	Handling missing values:
If I want to compare the temperatures, I need data for all cities and global data. For this reason, I decided to filtered out missing values and keep only data that has values for all selected cities and global data. I filtered out missing data and copy-paste selected data to new worksheet in order to work on data without missing values (alternatively I performed VLOOKUP technique on the data that has “the least data points” – in this case the null values are not transferred).

### Data Wrangling with Python in Jupyter Notebook  
1.	Read in data from excel file.
2.	Dropped unnecessary columns ‘city’ and ‘country’.
3.	Dropped null values, using dropna() function.
4.	Checked cleaned dataset, ensuring is ready for performing analysis.

## EDA & FEATURE ENGINEERING 

**Correlation coefficient**

Correlation coefficients are used to measure the strength and direction of a relationship between two variables (2). The value of the correlation coefficient varies between +1 and -1. As the correlation coefficient value goes towards 0, the relationship between the two variables will be weaker. The most common correlation measures used is Pearson R Correlation (3). A correlation between variables indicates that as one variable changes in value, the other variable tends to change in a specific direction.  Understanding that relationship is useful because we can use the value of one variable to predict the value of the other variable (4).

**Correlation and P value**
Correlation is a way to test if two variables have any kind of relationship, whereas p-value tells us if the result of an experiment is statistically significant (5). P-value evaluates how well data rejects the null hypothesis, which states that there is no relationship between two compared groups. Successfully rejecting this hypothesis tells you that your results may be statistically significant (6).

**Statistical Significance**
Statistical significance is the likelihood that the difference in conversion rates between a given variation and the baseline is not due to random chance. A result of an experiment is said to have statistical significance, or be statistically significant, if it is likely not caused by chance for a given statistical significance level (6).

**What's the correlation coefficient for this dataset?**
A great way to explore, to get familiar with the data, finding patterns and building intuitions is to calculate, visualize and uncover complex and unknown relationships between variables. 

**Calculating correlation coefficient**

I calculated correlation coefficient between year & global temperature and correlation between global average temperatures & local city temperatures and observed what kind of correlation (if any) exists. Calculation for correlation coefficient was made with Excel and Python.

-	Calculation in excel: Using `Data Analysis tool` from `Analysis tab`.
-	Calculation in Python: Using Pandas `corr()` function.
-
Correlation coefficient between year and global temperature is ***0.86***. This value indicates strong positive correlation, meaning, when the year change there is an increase (change) in the temperature.
Correlation coefficient between local city temperature and global temperature is ***0.62***. This value indicates positive correlation, but it is not a strong correlation.

**Visualizing Relationships**

<p align="center">
<img src="Graphics/ScatterPlot_global-year.png" width="30%" height="30%"> <img src="Graphics/ScatterPlot_LJ-year.png" width="30%" height="30%"> <img src="Graphics/ScatterPlot_global-LJ.png" width="30%" height="30%">
</p>

<p align="center">
<i>Figure 1: Relationship between global avg temp. and year. </i><br />
<i>Figure 2: Relationship between 5y moving average and year.</i><br /> 
<i>Figure 3: Relationship between global avg temp and avg. temp in Ljubljana. </i><br />
</p>

<p align="center">
<img src="Graphics/Coef_Heat_Map.png" width="30%" height="30%">
</p>

<p align="center">
Figure 4: Correlation Coefficient Heat Map.
</p>
