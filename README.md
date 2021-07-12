# Exploratory Data Analysis on the Automobile Data Set
## PURPOSE
To explore the automobile dataset(provided by Hyperiondev) attached in this repository in order to report findings.

## ANALYSIS
### 1)DATA CLEANING
Looking at the data set, it is first discovered that not all columns are relevant for the purpose of this report so a couple of unnecessary columns were dropped using **DataFrame.drop()** function in pandas.

Furthermore, **DataFrame.duplicated().sum()** function was used to check if there any duplicated rows of which none were found. 

To check if there are any outliers in the price distribution, a histogram was plotted.

### 2) DEALING WITH MISSING DATA
The function **DataFrame.isnull().sum()** is used to check if there are any null values and even though the function returned zero, the first inspection after loading the data set resulted in noticing some records presented as question marks(**?**). A check was made by selecting unique values columns using **DataFrame.Column.unique()** in order to make an assumption that **?** are all missing values and need to be dealt with. Therefore all **?** were replaced with NaN using **DataFrame.replace('?', np.nan, inplace=True )**. 

Upon knowledge of the existence of missing values, they were printed out using **print(df.isnull().sum())** to see number in each column and potted using **missingno.matrix(DataFrame)** 

The missing values were thereafter replaced with the median of the variable grouped by car make and body type.

### 3) DATA STORIES, VISUALIZATIONS & FINDINGS

* First we look at the number of cars by make in the dealership and find Toyota has most cars.
* Is it because Toyota is the cheapest car? To answer this question, we group makes and check average price to clearly see that the average price for Toyota cars is just below average but there are still way cheaper cars so we conclude the number of cars is not correlated to price.
* We can further look at how Top 10 most expensive cars compare with Top 10 cheapest cars. We also group by body type to see if it plays a role and learn that Mercedes-benz is the most is expensive car make and Subaru is the cheapest in terms of price averages. We also learn that most cheap cars are hatchbacks and most expensive cars are sedans
* grouping all makes and body type helps us also see that Toyota has the widest range of body types with average prices highest for converstibles and the rest being about equal.
* Lastly, we look at correlations between differnt variables and price to find, price increases with horsepower, engine-size and length but decreases with highway-mpg.


