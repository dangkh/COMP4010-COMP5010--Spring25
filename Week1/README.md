
# 🧪 Week 1 - Lab Exercise and Assignment

---


# 📑 Table of Contents


- [Section 1: Week 1 – Lab Exercise](#section-1-week-1--lab-exercise)
  - [Part 1: Setting Up](#part-1-setting-up)
  - [Exercise 1: Creating and Evaluating Data Visualisations with Python](#exercise-1-creating-and-evaluating-data-visualisations-with-python)
  - [Exercise 2: Advanced Visualisation Tasks](#exercise-2-advanced-visualisation-tasks)
    - [Task 1: Adding Details and Annotations to Charts](#task-1-adding-details-and-annotations-to-charts)
    - [Task 2: Combining Multiple Charts](#task-2-combining-multiple-charts)
    - [Task 3: Working with a Larger Dataset](#part-4-working-with-a-larger-dataset)
    - [Task 4: Reflection Questions](#part-5-reflection-questions)

- [Section 2: Week 1 – Lab Assignment](#section-2-week-1--lab-assignment)
  - [Task 1: Data Preprocessing](#task-1-data-preprocessing)
  - [Task 2: Data Visualisation](#task-2-data-visualisation)
  - [Task 3: Extreme Weather Events Analysis](#task-3-extreme-weather-events-analysis)
  - [Task 4: Investigate Correlation with CO₂ Emissions](#task-4-investigate-correlation-with-co₂-emissions)
  - [Submission Guidelines](#submission-guidelines)

---



---

# 🏋 Section 1: Week 1 – Lab Exercise

## 🛠Part 1: Setting Up


Follow these steps to set up your Jupyter environment for the Data Visualization labs. This guide ensures you have everything ready to create and analyze visualizations using Python.


### 🟡 Step 1: Install Python 3.13.2

1. **Download Python 3.13.2** from the [official website](https://www.python.org/downloads/).
2. **During installation**, check the box that says **"Add Python to PATH"**.
3. **Complete the installation.**

---


### 🟠 Step 2: Set Up a Virtual Environment

A virtual environment keeps your project dependencies separate from other Python projects.

#### 📂 Open your terminal/command prompt:

#### 📂 Create a Project Folder:
```bash
mkdir data_visualisation_lab
cd data_visualisation_lab
```

#### 🛡️ Create a Virtual Environment:
```bash
python -m venv venv
```

#### 🚀 Activate the Virtual Environment:
- On **Windows**:
```bash
venv\Scripts\activate
```
- On **macOS/Linux**:
```bash
source venv/bin/activate
```

---

### 🟢 Step 3: Install Jupyter and Required Libraries

#### 🚀 Upgrade `pip`:
```bash
python -m pip install --upgrade pip
```

#### 📘 Install Jupyter Notebook:
```bash
pip install notebook
```

#### 📊 Install Libraries for Data Visualisation:
```bash
pip install pandas matplotlib seaborn
```

---

### 🟤 Step 4: Launch Jupyter Notebook

#### 🌐 Start Jupyter Notebook:
```bash
jupyter notebook
```
A browser window will open. Navigate to your **`data_visualisation_lab`** folder.

- **Create a new notebook:** Click on `"New"` > `"Python 3"` to start coding.

---

### 🟣 Step 5: Verify Jupyter is Using the Correct Environment

#### ✅ Run this code in a new notebook cell:
```python
import sys
print(sys.executable)
```
**Check the output:** It should show a path ending with:
- `/venv/bin/python` (**macOS/Linux**)  
- `\venv\Scripts\python.exe` (**Windows**)

If the path is correct, your setup is complete! ✅

---

#### 🟠 Using Jupyter in Future Sessions

You don’t need to reinstall everything each time. Follow these steps to continue working each week:

1. **Open Terminal/Command Prompt.**
2. **Navigate to your project folder:**
   ```bash
   cd path_to_project/data_visualisation_lab
   ```
3. **Activate the virtual environment:**
   - On **Windows**:
     ```bash
     venv\Scripts\activate
     ```
   - On **macOS/Linux**:
     ```bash
     source venv/bin/activate
     ```
4. **Launch Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```

---

## ⚠️ Troubleshooting Tips

### 🧵 If Jupyter doesn't open in the browser:
Look for a link in the terminal that looks like this:
```
http://localhost:8888/?token=some_long_token_here
```
Copy and paste this link into your browser manually.

### ❌ If packages are missing:
- Ensure the virtual environment is activated before running Jupyter.
- If needed, reinstall missing packages:
```bash
pip install package_name
```

---

✅ **Setup Complete!** You are now ready to start your lab assignments. 🚀📊



---

## 🧪 Exercise 1: Creating and Evaluating Data Visualisations with Python

### 🎯 Objective:
By the end of this lab, you will:

- 📊 **Create basic visualisations**: Create basic visualisations (bar charts, line charts, scatter plots) using Python libraries.
- 🚫 **Identify and correct visualisation mistakes** 2.	Recognise and correct common visualisation mistakes (e.g., truncated axes, overloaded charts.)
- 🧐 **ompare good and bad visualisations and explain their impact on data interpretation**.

---

### 🟡 Part 1: Setting Up

#### 1️⃣ **Import Required Libraries**
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

#### 2️⃣ **Load Dataset (Sample Monthly Sales & Temperature Data)**
```python
# Example dataset
data = {
    'Month': ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
    'Sales': [200, 220, 250, 270, 300, 320],
    'Temperature': [30, 32, 35, 40, 42, 45]
}
df = pd.DataFrame(data)
df
```

---

### 🟠 Part 2: Creating Basic Charts

#### 📊 1️⃣ **Bar Chart: Monthly Sales**
```python
plt.figure(figsize=(8, 5))
sns.barplot(x='Month', y='Sales', data=df)
plt.title('Monthly Sales')
plt.show()
```

#### 📈 2️⃣ **Line Chart: Temperature Over Time**
```python
plt.figure(figsize=(8, 5))
sns.lineplot(x='Month', y='Temperature', data=df, marker='o')
plt.title('Monthly Temperature')
plt.show()
```

#### 📉 3️⃣ **Scatter Plot: Sales vs. Temperature**
```python
plt.figure(figsize=(8, 5))
sns.scatterplot(x='Temperature', y='Sales', data=df)
plt.title('Sales vs. Temperature')
plt.show()
```

---

### 🟢 Part 3: Identifying and Correcting Bad Visualisations

#### ⚠️ 1️⃣ **Truncated Y-Axis Example (Misleading)**
```python
plt.figure(figsize=(8, 5))
sns.barplot(x='Month', y='Sales', data=df)
plt.ylim(200, 350)  # Truncated Y-axis
plt.title('Truncated Axis: Misleading Sales Growth')
plt.show()
```
📌 **Task:** Explain how the truncated Y-axis exaggerates differences.  
✅ **Correction:** Reset the Y-axis to start at 0.

---

#### ⚠️ 2️⃣ **Overloaded Chart Example (Too Much Information)**
```python
plt.figure(figsize=(8, 5))
sns.lineplot(x='Month', y='Sales', data=df, label='Sales', marker='o')
sns.lineplot(x='Month', y='Temperature', data=df, label='Temperature', marker='s')
plt.title('Overloaded Chart: Too Much Information')
plt.legend()
plt.show()
```
📌 **Task:** Explain why this chart may confuse viewers.  
💡 **Suggestion:** Use separate charts or focus on one variable.

---

#### ⚠️ 3️⃣ **Misleading Pie Chart Example (Exaggerated Differences)**
```python
pie_data = [30, 40, 35]
labels = ['Product A', 'Product B', 'Product C']

plt.figure(figsize=(6, 6))
plt.pie(pie_data, labels=labels, explode=(0, 0.1, 0), autopct='%1.1f%%', startangle=90)
plt.title('Misleading Pie Chart: Exaggerated Differences')
plt.show()
```
📌 **Task:** Identify issues such as:
- 🎨 Use of 3D effects  
- 🧩 Slice exaggeration  
- 🏷️ Unclear labels  

💡 **Suggestion:** Propose a clearer alternative (e.g., a bar chart).

---

✅ **End of Lab Exercise 1**: You have now created and evaluated visualisations and identified potential pitfalls in charts. 🚀📊  

---

## 🧪 Exercise 2: Advanced Visualisation Tasks

### 🎯 Objective:
In this lab, you will:  
- 🖼️ Add details and annotations to charts.  
- 📊 Create subplots and overlay charts.  
- 📈 Work with real-world datasets to create visualisations.  
- 💡 Reflect on the impact of chart customisations and combining multiple visualisations.  

---

### 🟡 Task 1: Adding Details and Annotations to Charts

#### 🟠 1️⃣ Enhance the Bar Chart with Customisation
```python
plt.figure(figsize=(8, 5))
sns.barplot(x='Month', y='Sales', data=df, palette='Blues_d')

# Adding annotations
for index, row in df.iterrows():
    plt.text(index, row['Sales'] + 5, row['Sales'], ha='center')

plt.title('Monthly Sales with Annotations')
plt.xlabel('Month')
plt.ylabel('Sales')
plt.grid(axis='y', linestyle='--')
plt.show()
```

#### 🟠 2️⃣ Customise the Line Chart with Styles
```python
plt.figure(figsize=(8, 5))
sns.lineplot(x='Month', y='Temperature', data=df, marker='o', linestyle='--', color='red')

# Highlight the highest temperature
max_temp = df['Temperature'].max()
max_month = df[df['Temperature'] == max_temp]['Month'].values[0]
plt.annotate(f'Highest Temp: {max_temp}', xy=(max_month, max_temp), xytext=(max_month, max_temp + 2),
             arrowprops=dict(facecolor='black', shrink=0.05))

plt.title('Monthly Temperature with Highlights')
plt.xlabel('Month')
plt.ylabel('Temperature (C)')
plt.show()
```

---

### 🟢 Task 2: Combining Multiple Charts

#### 🟣 1️⃣ Create Subplots to Compare Sales and Temperature
```python
fig, ax = plt.subplots(2, 1, figsize=(10, 8))

sns.barplot(x='Month', y='Sales', data=df, ax=ax[0], palette='coolwarm')
ax[0].set_title('Monthly Sales')

sns.lineplot(x='Month', y='Temperature', data=df, marker='o', ax=ax[1], color='green')
ax[1].set_title('Monthly Temperature')

plt.tight_layout()
plt.show()
```

#### 🟣 2️⃣ Overlay Line and Bar Charts
```python
fig, ax1 = plt.subplots(figsize=(8, 5))

# Bar chart for Sales
sns.barplot(x='Month', y='Sales', data=df, ax=ax1, alpha=0.6, color='skyblue')
ax1.set_ylabel('Sales')

# Line chart for Temperature
ax2 = ax1.twinx()
sns.lineplot(x='Month', y='Temperature', data=df, ax=ax2, marker='o', color='red')
ax2.set_ylabel('Temperature (C)')

plt.title('Sales and Temperature Comparison')
plt.show()
```

---

### 🟤 Task 3: Working with a Larger Dataset

#### 📥 1️⃣ Download the COVID-19 Dataset
```python
url = 'https://covid.ourworldindata.org/data/owid-covid-data.csv'
covid_df = pd.read_csv(url)
covid_df.head()
```

#### 🧹 2️⃣ Filter Data for a Specific Country (e.g., Vietnam)
```python
vietnam_df = covid_df[covid_df['location'] == 'Vietnam']
vietnam_df = vietnam_df[['date', 'new_cases', 'new_deaths']].dropna()
vietnam_df['date'] = pd.to_datetime(vietnam_df['date'])
vietnam_df.head()
```

#### 📈 3️⃣ Visualise New COVID-19 Cases Over Time
```python
plt.figure(figsize=(12, 6))
sns.lineplot(data=vietnam_df, x='date', y='new_cases', color='blue')
plt.title('Daily New COVID-19 Cases in Vietnam')
plt.xlabel('Date')
plt.ylabel('New Cases')
plt.show()
```

#### 📊 4️⃣ Compare New Cases and New Deaths with Dual Axes
```python
fig, ax1 = plt.subplots(figsize=(12, 6))

sns.lineplot(data=vietnam_df, x='date', y='new_cases', ax=ax1, color='blue', label='New Cases')
ax1.set_ylabel('New Cases', color='blue')

ax2 = ax1.twinx()
sns.lineplot(data=vietnam_df, x='date', y='new_deaths', ax=ax2, color='red', label='New Deaths')
ax2.set_ylabel('New Deaths', color='red')

plt.title('COVID-19 New Cases and Deaths in Vietnam')
fig.tight_layout()
plt.show()
```

---

### 🟠 Task 4: Reflection Questions

#### 💡 1️⃣ **Customisation Impact:**  
- How did adding annotations and custom styles improve the clarity of your visualisations?  

#### 💡 2️⃣ **Combining Charts:**  
- What are the benefits and potential pitfalls of combining multiple data visualisations into one chart?  

#### 💡 3️⃣ **Real-World Dataset Challenges:**  
- What difficulties did you face when working with the COVID-19 dataset? How did you address them?  

---

✅ **Lab complete!** 🚀 ILab complete! If you haven’t changed the code by trying different examples, please do so. If you have done that, now move to the Lab Assignment. 🧪📊  


---

# 🏋 Section 2: Week 1 – Lab Assignment

## 📝 Week 1 – Lab Assignment: Real-World Data Visualisation Challenge

### 🗒️ NOTES:
1. ✅ **Before you start:** Complete the exercises in Week 1 – Lab Exercise.  
2. 📤 **Submission:** Upload your Jupyter Notebook (`.ipynb` file) to Canvas **before the end of this week**.

---

### 📌 Assignment Details

#### 🟡 Instructions:
- 🐍 Use **Python and Jupyter Notebook** to complete the tasks.  
- 💡 You may need to **research certain techniques** to solve the exercise fully.  
- 📝 Submit your Jupyter Notebook (`.ipynb` file) on Canvas.  
- 💬 **Document** all code cells with clear comments.  

---

### 🟠 Exercise: Analysing and Visualising Global Temperature Trends

#### 📂 Dataset:
- 📥 Download the **Global Land Temperature Data** from Kaggle:  
  👉 [Global Temperature Dataset (Kaggle)](https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data)  
  **Note:** Only use `GlobalLandTemperaturesByCountry.csv` file.

---

### 🟡 Task 1: Data Preprocessing

1️⃣ Load the dataset into a Pandas DataFrame.

2️⃣	Select data from a specific country of your choice.

3️⃣	Convert the date column to a datetime format and filter for data from the year 1900 onward.

4️⃣	Handle missing values: Decide on an appropriate strategy (e.g., drop, interpolate, or fill).

5️⃣	Create a new column for the average yearly temperature per country

---

### 🟠 Task 2: Data Visualisation

#### 1️⃣ **Line Chart:** Temperature Trend Over Time  
- 📈 Plot the **yearly average temperature** trend.  
- 🎨 Customise the chart with a **title, axis labels, and markers**.  

#### 2️⃣ **Rolling Average Chart:** 10-Year Rolling Average  
- 📊 Compute and plot **10-year rolling average**.  
- 📈 o	Overlay this rolling average on the original line chart.  

#### 3️⃣ **Compare Multiple Countries:**  
- 🌍 Select **three countries** and compare their trends on the **same chart**.  
- 🟦 Use **different line styles and colours** for each country.  

---

### 🟢 Task 3: Extreme Weather Events Analysis

#### 1️⃣ **Identify Top 5 Hottest and Coldest Years:**  

#### 2️⃣	Mark these years on your temperature trend chart witd **annotations**s.  

#### 3️⃣ **Plot Bar Chart:** showing the temperature difference between the hottest and coldest years.  


---

### 🟣 Task 4: Investigate Correlation with CO₂ Emissions

#### 📂 1️⃣ **Download the CO₂ Emissions Dataset:**  
👉 [OWID CO₂ Data](https://github.com/owid/co2-data) (`owid-co2-data.csv`)

#### 🗂️ 2️⃣ **Load and Preprocess the Data:**  
- 📑 Read the CO₂ dataset into a Pandas DataFrame.  
- 📑 Select relevant columns: `year`, `country`, and `co2`.  
- 🎯 Filter for the same country used in your temperature analysis.  


#### 🔗 3️⃣ **Merge Temperature Data with CO₂ Data:**  
- 🧹	Merge both datasets based on year and country.
- 🧹 Handle any missing values.  


#### 📊 4️⃣ **Create a Scatter Plot:**
-	📈 Plot CO₂ emissions vs. average temperature for the selected country.
-	📈 Label the axes and add a title.

#### 📈 5️⃣ **Fit a Linear Regression Line:**  
- 🟦 Use `seaborn`'s `regplot` to fit a regression line.  
-	Interpret the trend: Does CO₂ emission increase correlate with rising temperatures?


---

### 🚀 Submission Guidelines

📌 Ensure your Jupyter Notebook includes **all required charts and explanations**  
📂 **File Format:** `Week1_lab_assignment_YourID.ipynb`  
📤 **Upload to:** Canvas **before the deadline**.  
Back up data(https://drive.google.com/drive/u/0/folders/17NyHDvlhI1xbk80eIVQa9qa378yKMhK6)
---

🎯 **Good luck and happy coding!** 🚀📊  
