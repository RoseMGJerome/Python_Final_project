# Python_Final_project
Data anatylics for a Steel industry energy consumption

Dataset information
The data is collected from a smart small-scale steel industry in South Korea.
The information gathered is from the DAEWOO Steel Co. Ltd in Gwangyang, South Korea. It produces several types of coils, steel plates, and iron plates. The information on electricity consumption is held in a cloud-based system. The information on energy consumption of the industry is stored on the website of the Korea Electric Power Corporation (pccs.kepco.go.kr), and the perspectives on daily, monthly, and annual data are calculated and shown.

# Why this Dataset interests you and what you hope to find out in your data analysis for the final project?
Energy is one of the most important resources in our daily lives. I chose this dataset because it will help me understand how energy is used, when consumption is highest, and which factors are associated with energy usage.
This dataset is especially useful because it includes energy consumption, reactive power, power factor, CO₂ emissions, and time-related variables. In my analysis, I will focus on energy consumption patterns, differences between weekdays and weekends, indicators of electricity efficiency, identify 
peak consumption periods, and explore relationships between energy usage, reactive power, power factor, and CO₂ emissions.


# Summary

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
<img width="1678" height="782" alt="Screenshot 2026-11-13 025112" src="https://github.com/user-attachments/assets/d6d8db47-c97c-4171-a5f7-d1856c1d9a69" />


The dataset contains 10 columns and 35040 rows.
<img width="1321" height="457" alt="Screenshot 2026-11-12 212728" src="https://github.com/user-attachments/assets/93784817-d838-46b4-9eb9-1c859b4257f6" />


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

# Statistic analysis
<img width="1742" height="548" alt="Screenshot 2026-11-13 025717" src="https://github.com/user-attachments/assets/205fea16-cc29-4446-ba04-a14e83474a69" />


###Analysis!!!

How does electricity consumption differ between weekdays and weekends?
Which month has the highest average consumption?

Number of observations per load category.

Why is Load_Type important for our analysis?
Load_Type helps you understand how the factory's electricity demand changes according to its operating conditions.

When does the factory consume the most electricity?


## Data visualization!!


<img width="571" height="521" alt="fig1_Electricity_consumption_by_day_of_week" src="https://github.com/user-attachments/assets/62eac1eb-a328-4325-8fc3-a9297a318f3d" />
Electricity Consumption by Day of the Week
We observe lower energy consumption during the weekend, especially on Sundays. This may indicate that the company is closed on weekends or operates only a limited number of machines during those days.




<img width="562" height="455" alt="fig2_Average_electricity_per_month" src="https://github.com/user-attachments/assets/7784c6b8-f79b-43e3-949d-24dbeed50aca" />
January has the highest average energy consumption (kWh), followed by February. This may indicate that the company received more orders at the beginning of the year, possibly due to increased demand during the holiday season compared to other months.


<img width="589" height="455" alt="Frequency_of_load_type" src="https://github.com/user-attachments/assets/fa195023-3be6-4a9e-9061-156b6569c1dc" />
The factory requires a relatively small amount of electricity. This could happen when fewer machines are operating, production activity is lower, or some equipment is not being used.


<img width="996" height="470" alt="Hourly_energy_consumption_by_day_of_week" src="https://github.com/user-attachments/assets/97a324f5-fd6e-4cf9-be4d-74a8ebc636a1" />
![Hourly energy consumption by day of wee](Hourly_energy_consumption_by_day_of_week.png)
For this visualization, we chose a line plot to identify when the factory consumes the most electricity during the day and for differents days of the week. According to the graph, we can see that electricity consumption is high between 7:00 AM and 12:00 PM, decreases between 12:00 PM and 1:00 PM, and then increases significantly from 1:00 PM to 8:00 PM. This pattern might suggest that the factory operates from 7:00 AM to 8:00 PM, with a long break around noon.

This is a useful visualization because it helps us understand how average electricity consumption is distributed throughout the day.

### Correlation!!
Scatter Plot Analysis: Energy Consumption and CO₂ Emissions
A scatter plot can be used to visualize the relationship between energy consumption and CO₂ emissions. This visualization helps us identify whether higher electricity consumption is associated with higher CO₂ emissions.

<img width="576" height="455" alt="Energy_consumption_vs_C02_emissions" src="https://github.com/user-attachments/assets/8c893588-652b-4d70-803c-3e108d3d027e" />

This visualization helps us identify whether higher electricity consumption is associated with higher CO₂ emissions. The graph shows a strong positive relationship between electricity consumption and CO₂ emissions. In other words, as electricity consumption increases, CO₂ emissions also tend to increase. The data used in this analysis comes from DAEWOO Steel Co. Ltd. in Gwangyang, South Korea. The company produces several types of steel products, including coils, steel plates, and iron plates. I chose this graph to illustrate the relationship between these two variables and explore the potential environmental impact of the company's energy consumption.


