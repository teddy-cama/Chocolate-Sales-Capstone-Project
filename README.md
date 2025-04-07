# Chocolate Sales Capstone Project

This project was created as a practice exercise to learn and apply the fundamentals of data analysis, manipulation and visualization. I made use of python to achieve a set of problems and exercises given by an AI.

## Project Structure/
Chocolate Sales Capstone Project/
├── data/
│   └── Chocolate Sales.csv
├── notebooks/
│   └── Chocolate Sales.ipynb
├── README.md
└── LICENSE


## Data Source
I got the data from [https://www.kaggle.com/datasets/atharvasoundankar/chocolate-sales?resource=download]
Kaggle is a great site to get data sets to practice Data Analysis

## Problem given

Alright, let's treat this like a data analysis project. You've got a CSV file with product information, and there are many things we can do with it! Here's a breakdown of potential operations and analysis, as if I were your "boss" giving you tasks:

**Phase 1: Data Exploration and Cleaning (Essential First Steps)**

1.  **"First, I need you to understand the data. Load the CSV and give me a summary of each column. Tell me the data type, the number of missing values, and the number of unique values for each field."**
    * This involves using Python libraries like Pandas to read the CSV and perform basic data inspection.
    * Essentially, you'll need to use functions like `df.info()`, `df.isnull().sum()`, and `df.nunique()`.

2.  **"Next, we need to clean the data. Handle the missing values appropriately. For numeric fields like 'Price' and 'Stock', consider imputation or removal. For categorical fields like 'Color' or 'Category', decide on a strategy (e.g., fill with 'Unknown' or remove rows)."**
    * This requires you to make decisions based on the context.
    * Imputation (filling missing values) can be done using mean, median, or mode.
    * Removing rows with many missing values might be necessary.

3.  **"Check for inconsistencies in the 'Currency' and 'Price' fields. Ensure all prices are in a consistent currency (e.g., convert all prices to USD if necessary). Also, clean up any text fields like 'Description' or 'Name' by removing unnecessary whitespace or special characters."**
    * This step ensures data quality and consistency.
    * You might need to write functions to clean text.
    * You might need to use external api's to convert currency.

4.  **"Examine the 'Stock' and 'Availability' fields. Are they consistent? Do they provide redundant information? If so, decide which field is more reliable and consider removing the other."**
    * Sometimes, multiple fields convey similar information.

**Phase 2: Basic Analysis and Reporting**

5.  **"Provide a summary report of the distribution of products across different 'Categories' and 'Brands'. Show me the top 5 categories and brands with the highest product counts."**
    * This involves using `value_counts()` and plotting libraries like Matplotlib or Seaborn.

6.  **"Analyze the 'Price' distribution. Calculate the mean, median, and standard deviation of prices. Create a histogram to visualize the price distribution. Identify any outliers."**
    * This helps understand the pricing strategy and identify potential errors.

7.  **"Investigate the relationship between 'Category' and 'Price'. Are there any categories with significantly higher or lower average prices? Create box plots to visualize this relationship."**
    * This helps understand pricing per category.

8.  **"Show me the stock levels for each brand. Which brands have the most stock? Which brands have the least stock?"**
    * Helps understand inventory per brand.

**Phase 3: Advanced Analysis (If Time Permits)**

9.  **"Perform a correlation analysis between numeric fields like 'Price' and 'Stock'. Is there any relationship between these variables?"**
    * This helps understand potential correlations.

10. **"Analyze the 'Description' field using text analysis techniques. Identify the most common keywords or phrases used in product descriptions. This can help us understand customer preferences."**
    * This requires Natural Language Processing (NLP) techniques.

11. **"Create a dashboard that summarizes key metrics, such as total product count, average price, and stock levels. Include visualizations of product distribution across categories and brands."**
    * This helps present the findings in a clear and concise manner.

**Example Python Code Snippets (Illustrative)**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the CSV
df = pd.read_csv("your_file.csv")

# 1. Summary of each column
print(df.info())
print(df.isnull().sum())
print(df.nunique())

# 2. Handle missing values (example)
df['Price'].fillna(df['Price'].median(), inplace=True)
df['Color'].fillna('Unknown', inplace=True)

# 5. Category and brand distribution
print(df['Category'].value_counts().head(5))
print(df['Brand'].value_counts().head(5))

# 6. Price distribution
print(df['Price'].describe())
plt.hist(df['Price'])
plt.show()

# 7. Category vs. Price
sns.boxplot(x='Category', y='Price', data=df)
plt.xticks(rotation=90)
plt.show()

# 8. Stock per brand.
print(df.groupby('Brand')['Stock'].sum().sort_values(ascending = False))
```

**Remember:**

* Replace `"your_file.csv"` with the actual filename.
* These are just starting points. Adapt them to your specific needs.
* Document your steps and findings clearly.

Let me know when you've uploaded the file, and we can dive deeper into the specific tasks!


## Process and Workflow
*Note: I had already done most of the tasks before creating a repo, so I will make adjustments to the main file "Chocolate Sales.ipynb", separating it into other sections for easy understanding. All tasks are currently jam-packed into one file which is quite unreadable, so I'll group the tasks into different notebooks.*


 Capstone Project Analysing Chocolate Sales
