# 🧪 Week 2 - Lab Exercise and Assignment

---

# 📑 Table of Contents

- [Section 1: Week 2 – Lab Exercise](#section-1-week-2–-lab-exercise)
  - [Part 1: Working with a Simple DataFrame (Q1 - Q5)](#part-1-working-with-a-simple-dataframe-q1---q5)
  - [Part 2: Working with Real-World Datasets (Q6 - Q15)](#part-2-working-with-real-world-datasets-q6---q15)
  - [Part 3: Visualisation Using Pandas DataFrames (Q16 - Q20)](#part-3-visualisation-using-pandas-dataframes-q16---q20)

- [Section 2: Week 2 – Lab Assignment](#section-2-week-2–--lab-assignment)
  - [Part 1️: Data Cleaning & Exploration](#part-1️-data-cleaning--exploration)
  - [Part 2️: Aggregation & Filtering](#part-2️-aggregation--filtering)
  - [Part 3️: Advanced Data Processing](#part-3️-advanced-data-processing)
  - [Part 4: Data Visualisation (Q7 - Q9)](#part-4-data-visualisation-q7---q9)
  - [Submission Guidelines](#-submission-guidelines)
  
---

# 🏋 Section 1: Week 2 – Lab Exercise

## 📌 Instructions

This lab will guide you through 15 questions to practice Pandas operations.

**NOTE:** Remember to activate your Python environment (revise Week 1 – Lab Exercise).

The first 5 questions use a simple DataFrame to build your understanding.

The next 10 questions use real-world datasets:

- `GlobalLandTemperaturesByCountry.csv`
- `owid-co2-data.csv`
- `owid-covid-data.csv`

### 💡 Important:
- For COVID-19 data, focus on **2021** to avoid missing values.
- For CO₂ and temperature data, use years **before 2023** to get meaningful outputs.
- Repeat the examples with different values (e.g., different countries, time ranges).

---

## 🔹 Part 1: Working with a Simple DataFrame (Q1 - Q5)

### **Q1: Create and Display a DataFrame**
```python
import pandas as pd

# Sample DataFrame
df = pd.DataFrame({
    'Name': ['Alice', 'Bob', 'Charlie', 'David', 'Eva'],
    'Age': [25, 30, 35, 40, 22],
    'City': ['London', 'Paris', 'Berlin', 'Madrid', 'Rome']
})

print(df)
```

 🧐 **Question**: What are the column names? How are the rows indexed by default?
 
### **Q2: Select Specific Columns and Rows**
```python

# Select the 'Name' and 'Age' columns
df_subset = df[['Name', 'Age']]
print(df_subset)

# Select the row for 'Charlie' using .loc[]
charlie_row = df.loc[2]
print(charlie_row)

```

 🧐 **Question**: What is the difference between selecting with ```df[['Name', 'Age']]``` and ```df['Name']```?
 
 
### **Q3: Add and Delete a Row**
```python
# Adding a new row
df.loc[5] = ['Frank', 28, 'Amsterdam']
print(df)

# Deleting Bob's row
df = df.drop(1)
print(df)

```

 🧐 **Question**: Why do we assign ```df = df.drop(1)``` instead of just using ```df.drop(1)```?
 
### **Q4: Filtering and Sorting**
```python
# Select only people older than 30
df_filtered = df[df['Age'] > 30]
print(df_filtered)

# Sorting by Age in descending order
df_sorted = df.sort_values(by='Age', ascending=False)
print(df_sorted)

```

 🧐 **Question**: What happens if you change ```ascending=False``` to ```ascending=True```?
 
### **Q5: Grouping and Aggregation**
```python
# Grouping by City and calculating average Age
df_grouped = df.groupby('City')['Age'].mean()
print(df_grouped)


```

 🧐 **Question**: What does ```groupby('City')['Age'].mean()``` do?

---

## 🟠 Part 2: Working with Real-World Datasets (Q6 - Q15)
 
📌 Load the Datasets
```python

# Load datasets
df_temp = pd.read_csv('GlobalLandTemperaturesByCountry.csv')
df_co2 = pd.read_csv('owid-co2-data.csv')
df_covid = pd.read_csv('owid-covid-data.csv')
```
________________________________________

### **Q6: Exploring the COVID-19 Data**
```python
# Display dataset info
print(df_covid.info())
# Select COVID-19 data for 2021
df_covid = df_covid[df_covid['date'].str.startswith('2021')]
print(df_covid.head())
```
🧐 **Question**: What percentage of rows contain missing values?
________________________________________

### **Q7: Filtering COVID-19 Data for a Specific Country**
```python

# Select data for Vietnam in 2021
df_vietnam = df_covid[df_covid['location'] == 'Vietnam']
print(df_vietnam.tail())
```

🧐 **Question**: What is the total number of COVID-19 cases recorded in Vietnam in 2021?
________________________________________

### **Q8: Handling Missing Values in COVID-19 Data**
```python

# Fill missing values in new_cases with 0
df_covid['new_cases'] = df_covid['new_cases'].fillna(0)

# Drop rows where total_cases is NaN
df_covid = df_covid.dropna(subset=['total_cases'])
```
🧐 **Question**: What impact does filling missing values with 0 have on the dataset?
________________________________________

### **Q9: Exploring CO₂ Emissions Data**
```python

# Select CO₂ data for 2021
df_co2 = df_co2[df_co2['year'] == 2021]

# Display the top 5 rows
print(df_co2.head())
```
🧐 **Question**: What are the top 5 countries with the highest CO₂ emissions in 2021?
________________________________________

### **Q10: Finding the Highest and Lowest CO₂ Emissions**
```python

# Find the country with the highest CO₂ emissions
highest_co2 = df_co2[df_co2['co2'] == df_co2['co2'].max()]
print(highest_co2)
```
🧐 **Question**: What country had the lowest recorded CO₂ emissions in 2021?
________________________________________

### **Q11: Exploring Temperature Data**
```python

# Select only temperature data from before 2023
df_temp = df_temp[pd.to_datetime(df_temp['dt']).dt.year < 2023]

# Display dataset info
print(df_temp.info())
```
🧐 **Question**: What are the top 3 hottest recorded years?
________________________________________

### **Q12: Handling Missing Temperature Data**
```python

# Drop rows where AverageTemperature is NaN
df_temp = df_temp.dropna(subset=['AverageTemperature'])

print(df_temp.head())
```
🧐 **Question**: What happens to the dataset size after dropping NaN values?
________________________________________

### **Q13: Grouping Temperature Data by Country**
```python

# Find the average temperature for each country
df_avg_temp = df_temp.groupby('Country')['AverageTemperature'].mean()
print(df_avg_temp.head())
```
🧐 **Question**: What country had the highest average temperature?
________________________________________

### **Q14: Sorting Temperature Data**

```python
# Sorting by temperature in descending order
df_sorted_temp = df_avg_temp.sort_values(ascending=False)
print(df_sorted_temp.head(10))
```

🧐 **Question**: What are the top 10 hottest countries?
________________________________________

### **Q15: Exporting Cleaned Data to CSV**
```python

df_co2.to_csv('cleaned_co2_data.csv', index=False)
df_covid.to_csv('cleaned_covid_data.csv', index=False)
df_temp.to_csv('cleaned_temp_data.csv', index=False)
```
🧐 **Question**: Why is it useful to export cleaned datasets?


## 🔹 Part 3: Visualisation Using Pandas DataFrames (Q16 - Q20)
**NOTE:** Pandas allows us to generate basic visualisations directly using .plot(). In this section, you will create visualisations using Pandas and avoid missing values to ensure meaningful insights.
Before starting, install Matplotlib if needed:

```bash
pip install matplotlib
```

Import Matplotlib at the start of your script:

```python

import matplotlib.pyplot as plt
```
________________________________________

### **Q16: Plot CO₂ Emissions Over Time for a Specific Country**
Use the ```owid-co2-data.csv``` file and filter data for a country of your choice (e.g., United Kingdom).
```python

# Load CO₂ data
df_co2 = pd.read_csv('owid-co2-data.csv')

# Select data for a specific country and filter years before 2023
df_uk_co2 = df_co2[(df_co2['country'] == 'United Kingdom') & (df_co2['year'] < 2023)]

# Drop rows with missing CO₂ values
df_uk_co2 = df_uk_co2.dropna(subset=['co2'])

# Plot CO₂ emissions over time
df_uk_co2.plot(x='year', y='co2', kind='line', title='CO₂ Emissions in the UK Over Time')
plt.xlabel('Year')
plt.ylabel('CO₂ Emissions (Million Tonnes)')
plt.show()
```
🧐 **Question**: What trends do you notice in CO₂ emissions?
________________________________________

### **Q17: Bar Chart - Top 10 CO₂ Emitting Countries (2021)**
```python

# Select only 2021 data
df_co2_2021 = df_co2[df_co2['year'] == 2021]

# Drop NaN values in CO₂ emissions
df_co2_2021 = df_co2_2021.dropna(subset=['co2'])

# Get top 10 emitting countries
df_top10_co2 = df_co2_2021.sort_values(by='co2', ascending=False).head(10)

# Plot a bar chart
df_top10_co2.plot(x='country', y='co2', kind='bar', title='Top 10 CO₂ Emitting Countries in 2021')
plt.xlabel('Country')
plt.ylabel('CO₂ Emissions (Million Tonnes)')
plt.xticks(rotation=45)
plt.show()
```
🧐 **Question**: Which countries contributed the most to CO₂ emissions in 2021?
________________________________________

### **Q18: Temperature Trends Over Time for a Country**
Use the ```GlobalLandTemperaturesByCountry.csv``` dataset.
```python

# Load temperature data
df_temp = pd.read_csv('GlobalLandTemperaturesByCountry.csv')

# Convert date column to datetime
df_temp['dt'] = pd.to_datetime(df_temp['dt'])

# Filter for a specific country and years before 2023
df_uk_temp = df_temp[(df_temp['Country'] == 'United Kingdom') & (df_temp['dt'].dt.year < 2023)]

# Drop NaN values
df_uk_temp = df_uk_temp.dropna(subset=['AverageTemperature'])

# Plot temperature trends
df_uk_temp.plot(x='dt', y='AverageTemperature', kind='line', title='Temperature Trends in the UK')
plt.xlabel('Year')
plt.ylabel('Average Temperature (°C)')
plt.show()
```
🧐 **Question**: Can you identify warming trends in the UK?
________________________________________

### **Q19: COVID-19 Cases vs. Deaths (2021) - Scatter Plot**
Use the ```owid-covid-data.csv``` dataset and focus on 2021.
```python

# Load COVID-19 data
df_covid = pd.read_csv('owid-covid-data.csv')

# Select only 2021 data and drop NaNs
df_covid_2021 = df_covid[df_covid['date'].str.startswith('2021')].dropna(subset=['total_cases', 'total_deaths'])

# Plot scatter plot
df_covid_2021.plot(x='total_cases', y='total_deaths', kind='scatter', title='COVID-19 Cases vs. Deaths (2021)')
plt.xlabel('Total Cases')
plt.ylabel('Total Deaths')
plt.show()
```
🧐 **Question**: Is there a correlation between total cases and total deaths?
________________________________________

### **Q20: Comparing CO₂ Emissions and Temperature Change for a Country**
This combines data from two datasets (CO₂ and Temperature) to explore their relationship.
```python

# Merge CO₂ and temperature data on year
df_uk_co2['year'] = df_uk_co2['year'].astype(int)  # Ensure year is an integer
df_uk_temp['year'] = df_uk_temp['dt'].dt.year

# Group temperature data by year
df_uk_avg_temp = df_uk_temp.groupby('year')['AverageTemperature'].mean().reset_index()

# Merge datasets
df_combined = pd.merge(df_uk_co2, df_uk_avg_temp, on='year', how='inner')

# Drop NaN values
df_combined = df_combined.dropna(subset=['co2', 'AverageTemperature'])

# Plot CO₂ vs Temperature
df_combined.plot(x='co2', y='AverageTemperature', kind='scatter', title='CO₂ vs Temperature in the UK')
plt.xlabel('CO₂ Emissions (Million Tonnes)')
plt.ylabel('Average Temperature (°C)')
plt.show()
```
🧐 **Question**: Does increasing CO₂ correlate with rising temperatures?

✅ Lab complete! If you haven’t changed the code by trying different examples, please do so. If you have done that, now move to the Lab Assignment.


---

# 🏋 Section 2: Week 2 – Lab Assignment

### 🗒️ NOTES:
1. ✅ **Before you start:** Complete the exercises in Week 12– Lab Exercise.  
2. 📤 **Submission:** Upload your Jupyter Notebook (`.ipynb` file) to Canvas **before the end of this week**.

---

### 📌 Assignment Details

#### 🟡 Rules:

- 💬 The code must be fully commented.  
-	📝 Print all outputs so results are clearly visible.
-	🐍 Use Pandas and Matplotlib to complete the tasks.
-	🚫 Do not use NaN values—filter or replace missing data where necessary.
-	✅ Your final script should run without errors when executed.


#### 📂 Datasets:
Use one or more of the following (you should have those already from Week 1, if not ask the staff available at the lab):
```GlobalLandTemperaturesByCountry.csv```,```wid-co2-data.csv```, ```owid-covid-data.csv```

---


## 🔹 Part 1️ Data Cleaning & Exploration
💡 Objective: Prepare and clean the dataset before analysis.

### **Q1. Choose one dataset (CO₂, COVID, or Temperature) and clean it by:**
-	🧹 Removing all rows with missing values for key columns.
-	Filtering only data before 2023 (to avoid incomplete data).
-	Keeping only relevant columns that will be useful for analysis.

### **Q2. Display basic summary statistics using .describe().y**
- 🔍 What are the minimum, maximum, and average values for key numerical columns?
-	Check for missing values using .isna().sum() and confirm they were removed.

________________________________________

## 🔹 Part 2️ Aggregation & Filtering
💡 Objective: Extract meaningful insights from the dataset.

### **Q3. Identify the top 5 countries or regions based on a key metric:**
-	If working with CO₂ → Select the highest CO₂-emitting countries in 2021.
-	If working with Temperature → Find the countries with the highest average temperature before 2023.
-	If working with COVID → Find the 5 worst-affected countries in 2021 based on total cases or deaths.


### **Q4. Find the average value of a key metric per year using .groupby()**
-	If using CO₂, find the average CO₂ emissions per year.
-	If using Temperature, calculate yearly average temperatures.
-	If using COVID, find new cases per year.
-	📈 Display results as a DataFrame, showing the yearly trend.

________________________________________

## 🔹 Part 3: Advanced Data Processing

💡 Objective: Apply transformations and enhance the dataset.

### **Q5. Add a new column that shows percentage change in a key metric year-over-year**
-	Example: If using CO₂, calculate percentage change in CO₂ emissions per year.
-	Example: If using Temperature, calculate percentage change in average temperature per year.
-	Example: If using COVID, calculate percentage change in total cases per year.

💡 Hint: Use .pct_change() to compute the percentage difference between years.

### **Q6. Merge this dataset with another dataset (if applicable).**
-	Example: Merge CO₂ data with temperature data for the same country.
-	Example: Merge COVID data with population data (if the dataset contains population figures).
-	Ensure that the merged dataset only includes years with available data in both datasets.

________________________________________

## 🔹 Part 4: Data Visualisation (Q7 - Q9)

### **Q7: Line Chart - Trend Over Time**
💡 Objective: Create a line chart showing how a key metric has changed over time.

-	🔍 Select a country or region and plot the trend of one metric (e.g., CO₂ emissions, temperature, COVID cases).
-	The x-axis should represent the year, and the y-axis should represent the chosen metric.
-	Add labels, a title, and a legend to make the chart meaningful.

Example Questions:

-	How have CO₂ emissions in the UK changed over the years?
-	How has the global average temperature fluctuated over time?
-	How did COVID cases in Vietnam evolve throughout 2021?

📌 Deliverable: A line chart showing the selected trend.

________________________________________

### **Q8: Bar Chart - Top Contributors**
💡 Objective: Use a bar chart to compare top contributors for a key metric in a given year.

-	🔍Identify the top 10 contributors (countries or regions) for a chosen metric.
-	The x-axis should represent the country or region, and the y-axis should represent the metric value.
-	Use a single year to make the comparison meaningful (e.g., CO₂ emissions in 2021).
-	Rotate the x-axis labels if necessary for readability.

Example Questions:

-	Which 10 countries had the highest CO₂ emissions in 2021?
-	Which 10 countries had the highest temperatures before 2023?
-	Which 10 countries had the highest COVID cases in 2021?

📌 Deliverable: A bar chart comparing the top 10 contributors for a metric.

________________________________________

### **Q9: Scatter Plot - Relationship Between Two Metrics**

💡 Objective: Explore correlation between two variables using a scatter plot.

-	👉 Select two related metrics from a dataset.
-	The x-axis should represent one variable, and the y-axis should represent the other.
-	Ensure that the dataset does not contain NaN values for these metrics.
-	Fit a trend line (optional) to show possible correlations.

Example Questions:

-	Does higher CO₂ emissions correlate with higher temperatures?
-	Does a country's population size affect total CO₂ emissions?
-	Is there a link between COVID cases and total deaths per country?

📌 Deliverable: A scatter plot showing the relationship between two metrics.


### 🚀 Submission Guidelines

📌 Ensure your Jupyter Notebook includes **all required charts and explanations**  
📂 **File Format:** `Week2_lab_assignment_YourID.ipynb`  
📤 **Upload to:** Canvas **before the deadline**.  

---

🎯 **Good luck and happy coding!** 🚀📊  

