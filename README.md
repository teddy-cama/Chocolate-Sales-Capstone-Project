# Chocolate Sales Capstone Project

This project was created as a practice exercise to learn and apply the fundamentals of data analysis, manipulation and visualization. I made use of python to achieve a set of problems and exercises given by an AI.

## Project Structure/
Chocolate Sales Capstone Project/

├── data/

│   └── Chocolate Sales.csv

├── notebooks/

├── ├── Chocolate Sales.csv

├── ├── Cleaned Chocolate Sales.ipynb

├── ├── Cleaned Chocolate Sales.csv

├── └── Chocolate Sales.ipynb

├── README.md

└── LICENSE


## Data Source
I got the data from [https://www.kaggle.com/datasets/atharvasoundankar/chocolate-sales?resource=download]
Kaggle is a great site to get data sets to practice Data Analysis

## Problem given

Excellent! You've provided a clear summary of your sales data. Let's get to work. Here are a bunch of tasks to analyze your sales data, structured to build your skills progressively:

**Phase 1: Basic Exploration and Cleaning**

1.  **"Convert the 'Date' column to datetime objects. This will allow us to perform time-based analysis. Then tell me the earliest and latest date in the dataset."**
    * Use `pd.to_datetime()` to convert the column.
    * Use `.min()` and `.max()` on the datetime column.

2.  **"Check for unique values in the 'Country', 'Product', and 'Sales Person' columns. How many unique values are there in each column?"**
    * Use `.nunique()` to get the count.
    * Use `.unique()` to see the unique values themselves if needed.

3.  **"Analyze the 'Amount' and 'Boxes Shipped' columns. Calculate the descriptive statistics (mean, median, standard deviation, min, max, etc.). Are there any outliers?"**
    * Use `.describe()` to get the statistics.
    * Use histograms or box plots to visualize the distributions and identify outliers.

4.  **"Check for any inconsistencies in the 'Currency' column. Are all transactions in the same currency? If not, investigate and handle the differences if needed. If there are multiple currencies, inform me of the conversion rates to a single currency, for example, USD."**
    * Use `.unique()` and `.value_counts()` to understand the currencies.

5.  **"Create a new column called 'Amount per Box' by dividing the 'Amount' column by the 'Boxes Shipped' column. Then analyze the distribution of this new column."**
    * This helps understand the price per box.

**Phase 2: Basic Analysis and Reporting**

6.  **"Calculate the total sales 'Amount' and 'Boxes Shipped' for each 'Country'. Which country has the highest sales? Which country has the most boxes shipped?"**
    * Use `groupby()` and `sum()`.

7.  **"Calculate the total sales 'Amount' and 'Boxes Shipped' for each 'Product'. Which product is the best seller in terms of amount? Which product has the highest number of boxes shipped?"**
    * Use `groupby()` and `sum()`.

8.  **"Calculate the total sales 'Amount' and 'Boxes Shipped' for each 'Sales Person'. Who is the top sales person?"**
    * Use `groupby()` and `sum()`.

9.  **"Analyze sales over time. Calculate the total sales 'Amount' per month. Create a line plot to visualize the trend."**
    * Extract the month from the 'Date' column.
    * Use `groupby()` and `sum()`.
    * Use `matplotlib` or `seaborn` for plotting.

10. **"Analyze sales by 'Country' and 'Product'. Create a pivot table or a grouped bar chart to visualize the sales 'Amount' for each product in each country."**
    * Use `pivot_table()` or `groupby()` and `unstack()`.

**Phase 3: Advanced Analysis (If Time Permits)**

11. **"Calculate the average 'Amount per Box' for each 'Product' and 'Country'. Are there any significant differences in price per box across different regions or products?"**
    * Use `groupby()` and `mean()`.

12. **"Perform a time series analysis to identify any seasonal patterns or trends in sales. Decompose the time series into trend, seasonality, and residual components."**
    * Use `statsmodels` library for time series decomposition.

13. **"Identify the top 3 Sales Persons in each country based on sales amount. Produce a table that shows this information."**
    * Use `groupby()`, `apply()`, and `nlargest()`.

14. **"Create a dashboard that summarizes the key findings. Include visualizations of sales by country, product, and sales person, as well as the time series analysis."**
    * Consider using libraries like `plotly` or `dash` for interactive dashboards.

Remember to replace `"your_sales_data.csv"` with your actual filename. Let me know how it goes and if you have any questions!



## Process and Workflow
*Note: I had already done most of the tasks before creating a repo, so I will make adjustments to the main file "Chocolate Sales.ipynb", separating it into other sections for easy understanding. All tasks are currently jam-packed into one file which is quite unreadable, so I'll group the tasks into different notebooks.*

### Step One: Loading the Data Set
- With pd.load_csv() I loaded the data set as df.
 I used df.info() to get information about the data set.
    
    **Problem(s) Encountered.**
    - Could not read the CSV file which was in the 'data' folder.
        - *Tried:*
            *"read_csv(../data/'Chocolate Sales.csv')"*
            *No success.*
        - *Tried:*
            *"data_dir = 'data'*
            *file_name = Chocolate Sales.csv'*
            *file_path = os.path.join(data_dir, Chocolate Sales.csv)*
            *df = pd.read_csv(file_path)".*
            *No success*
        - *Tried:*
            *file_path = 'C:\Users\HP\Documents\GitHub\Data Analysis Projects\Chocolate-Sales-Capstone-Project\data'*
            *df = pd.read_csv(file_path)*
            *No Success*
        - *Temporary Solution*
            *Copied the data into the notebook folder, and load normally.*

### Step Two: Cleaning the Data Set
- From the data given in the information, I can see that the values for 'Amount' are all objects. I have to convert them into integers to make them workable.
I create a new column and make it all the currency values without the dollar sign.
With lambda, we eliminate the dollar sign from all values.
    **Problem Encountered.**
        - Values still cannot be recognized as strings due to the commas.
            - *Tried:*
                *Converting the all values in the column to strings, then replaced all commas with spaces, and removed the spaces.*

- Converted the string numerical values using the lambda function.
- Mirrored the Values onto the 'Amount' column.
- Renamed the Amount column.
- Dropped the Integer Amount Column
- Exported the dataframe as "Cleaned Chocolate Sales.csv"

### Phase 1: Basic Exploration and Cleaning

1.  **"Convert the 'Date' column to datetime objects. This will allow us to perform time-based analysis. Then tell me the earliest and latest date in the dataset."**
    * Use `pd.to_datetime()` to convert the column.
    * Use `.min()` and `.max()` on the datetime column.
- Converted the dates from "04-Jan-22" to a usable python format; "2022-01-04" for easy data retrieval.
- Our Earliest Shipment Date was on "2022-01-03".
- Our Latest Shipment Date was "2022-08-31".

2.  **"Check for unique values in the 'Country', 'Product', and 'Sales Person' columns. How many unique values are there in each column?"**
    * Use `.nunique()` to get the count.
    * Use `.unique()` to see the unique values themselves if needed.
***using the above functions, we see that:***

- there are 6 different countries we export to; 'UK', 'India', 'Australia', 'New Zealand', 'USA', 'Canada'
- there are 22 different products we have on the market; 'Mint Chip Choco',
        '85% Dark Bars', 'Peanut Butter Cubes',
        'Smooth Sliky Salty', '99% Dark & Pure', 'After Nines',
       '50% Dark Bites', 'Orange Choco', 'Eclairs', 'Drinking Coco',
       'Organic Choco Syrup', 'Milk Bars', 'Spicy Special Slims',
       'Fruit & Nut Bars', 'White Choc', 'Manuka Honey Choco',
       'Almond Choco', 'Raspberry Choco', 'Choco Coated Almonds',
       "Baker's Choco Chips", 'Caramel Stuffed Bars', '70% Dark Bites'
- there are 25 Sales Persons;'Jehu Rudeforth', 'Van     Tuxwell',
        'Gigi Bohling', 'Jan Morforth',
       'Oby Sorrel', 'Gunar Cockshoot', 'Brien Boise',
       'Rafaelita Blaksland', 'Barr Faughny', 'Mallorie Waber',
       'Karlen McCaffrey', "Marney O'Breen", 'Beverie Moffet',
       'Roddy Speechley', 'Curtice Advani', 'Husein Augar', 'Kaine Padly',
       'Dennison Crosswaite', "Wilone O'Kielt", 'Andria Kimpton',
       'Kelci Walkden', 'Camilla Castle', 'Madelene Upcott',
       'Dotty Strutley', 'Ches Bonnell'


 Capstone Project Analysing Chocolate Sales
