# Python_Final_project
Data anatylics for a Steel industry energy consumption

Dataset information
The data is collected from a smart small-scale steel industry in South Korea.
The information gathered is from the DAEWOO Steel Co. Ltd in Gwangyang, South Korea. It produces several types of coils, steel plates, and iron plates. The information on electricity consumption is held in a cloud-based system. The information on energy consumption of the industry is stored on the website of the Korea Electric Power Corporation (pccs.kepco.go.kr), and the perspectives on daily, monthly, and annual data are calculated and shown.


Summary

● Ingest the Data
● Data cleaning
● Data manipulation
● Data visualization
● Statistical analysis

We will use the Pandas library to import the dataset into Python and convert it into a DataFrame. We will perform data cleaning  and document each step of the process by adding comments to our code.
We will also manipulate the dataset by performing operations such as filtering, sorting, and grouping.We need to create at least three visualizations that help explain the key insights from the dataset using either Matplotlib or Seaborn. We should choose appropriate types of charts and customize the 
visualizations to make the results clear and easy to understand.
At the end of the project, we will conduct a statistical analysis that includes descriptive statistics, such as the median, mean, standard deviation, and mode, as well as correlation analysis. We also need to explain the purpose of each analysis and how it helps us understand the dataset.

Importing the dataset!!!
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df2 = pd.read_csv("Steel_industry_data.csv")
df2

Data cleaning!!!

Identifying duplicates data

df2.loc[ df2.duplicated(subset=['NSM', 'Usage_kWh', 'Day_of_week'])]
We have used three columns (NSM, Usage_kWh, and Day_of_week) to identify duplicate records in the dataset. The results reveal a considerable number of duplicate records based on these three columns.

Dropping duplicates and null values!!

df2.drop_duplicates(subset=['NSM', 'Usage_kWh', 'Day_of_week'], inplace=True)
df2.dropna(inplace=True)
After identifying the duplicate rows and missing values, we use the code above to remove them. Duplicate records and missing values can affect the accuracy and reliability of our data analysis.

Identifying outliers!!!

Comparing the Z-scores against the threshold of 3 reveals that the dataset contains potential outliers (Z-score > 3).

Identifying and handling outliers is an important step in data analytics because they can distort statistical analyses, reduce model accuracy, and lead to misleading conclusions.
