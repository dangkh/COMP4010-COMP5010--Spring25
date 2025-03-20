# 🧪 Week 5 - Lab Exercise and Assignment

---

# 📑 Table of Contents

- [Section 1: Lab Exercise](#section-1-lab-exercise)
  - [Tasks](#tasks)
- [Section 2: Lab Assignment](#section-2-lab-assignment)
  - [Submission Guidelines](#submission-guidelines)
  
  
---

# 🏋 Section 1: Lab Exercise

## 📌 Objective

In this lab, you will implement  **interactive data visualizations** using Python. You will apply: 

1.	Filtering: Allow users to refine the dataset using dropdown selections. 
2.	Drill-down: Enable hierarchical navigation (e.g., Year → Month). 
3.  Interactive Charts: Create dynamic bar charts and line charts that update based on user interactions. 

This lab will help you understand how interactive visualizations **enhance data exploration and decision-making.**

---

#### 📂 Datasets:

For this exercise, we will use a **Sales Transactions dataset**. 

If you do not have a dataset, you can download a sample dataset from: 📌 [Kaggle - Sample Superstore Sales Data](https://www.kaggle.com/datasets/bravehart101/sample-supermarket-dataset )

Alternatively, create a sample dataset using the following Python code: 

```python
import pandas as pd 
import numpy as np 
# Generate a sample dataset 
np.random.seed(1009) 
dates = pd.date_range(start="2020-01-01", periods=300, freq="D") 
regions = ["North America", "Europe", "Asia", "Australia"] 
categories = ["Electronics", "Clothing", "Home Goods", "Toys"] 
sales_amount = np.random.randint(100, 10000, size=len(dates)) 

df = pd.DataFrame({ 

    "Date": np.random.choice(dates, size=len(dates)), 

    "Region": np.random.choice(regions, size=len(dates)), 

    "Category": np.random.choice(categories, size=len(dates)), 

    "Sales": sales_amount 

}) 
df.to_csv("sales_data.csv", index=False) 
print("Sample dataset saved as 'sales_data.csv'.") 
```

The Kaggle dataset contains sales transactions with four columns: 

- Date (YYYY-MM-DD format) 
- Region (Sales from different regions) 
- Category (Product type) 
- Sales (Revenue generated) 

## 📋 **Tasks**: 

### 🔹 Task 1: Load the dataset 

Run the following code to load the dataset and inspect the first few rows: 
✅ Step 1: load the dataset
```python
df = pd.read_csv("sales_data.csv") 
print(df.head()) 
```

✅ Step 2: Create a Basic Visualization 
```python 

import plotly.express as px 
 
# Aggregate total sales per category 
sales_by_category = df.groupby("Category")["Sales"].sum().reset_index() 

# Create a bar chart 
fig = px.bar(sales_by_category, x="Category", y="Sales", title="Total Sales by Category") 

# Show the chart 
fig.show() 
```


### 🔹 Task 2: Modify the chart to show sales per region instead of category. 

✅ Step 1: Implement Filtering (Dropdown Selection) 

Now, let’s allow users to filter sales by region. We will use Dash to create an interactive dashboard. 

```python 
import dash 
from dash import dcc, html 
from dash.dependencies import Input, Output 
import plotly.express as px 

# Initialize Dash app 
app = dash.Dash(__name__) 

# App Layout 
app.layout = html.Div([ 
    html.H1("Interactive Sales Dashboard"), 
    # Dropdown for region selection 
    dcc.Dropdown( 
        id="region-filter", 
        options=[{"label": r, "value": r} for r in df["Region"].unique()], 
        value="North America", 
        clearable=False, 
    ), 
    # Graph output 
    dcc.Graph(id="sales-chart"), 
]) 

# Callback to update chart based on selection 
@app.callback( 
    Output("sales-chart", "figure"), 
    [Input("region-filter", "value")] 
) 

def update_chart(selected_region): 
    filtered_df = df[df["Region"] == selected_region] 
    sales_by_category = filtered_df.groupby("Category")["Sales"].sum().reset_index() 
    fig = px.bar(sales_by_category, x="Category", y="Sales", title=f"Sales in {selected_region}") 
    return fig 

# Run the app 
if __name__ == "__main__": 
    app.run_server(debug=True) 
```

### 🔹 Task 3: Modify the dropdown to allow selecting multiple regions. 

✅ Step 1: Implement Drill-down (Year → Month) 

Let’s create a drill-down system where: 

The first chart shows total sales per year 

Clicking on a year updates a second chart to show monthly sales 

```python 
# Convert Date column to datetime 
df["Date"] = pd.to_datetime(df["Date"]) 
df["Year"] = df["Date"].dt.year 
df["Month"] = df["Date"].dt.month 

# Aggregate yearly sales 
yearly_sales = df.groupby("Year")["Sales"].sum().reset_index() 

# Create interactive figure 
fig = px.bar(yearly_sales, x="Year", y="Sales", title="Yearly Sales") 

fig.show() 
```
---

### 🔹 Task 4: Modify the code so that clicking on a year updates a second chart to display monthly sales. 

What’s Next? 

Once you complete the exercise, move on to solving the assignment 🚀. 


---

# 🏋 Section 2: Lab Assignment

### 🗒️ NOTES:
1. ✅ **Before you start:** Complete the exercises in Week 5 Lab Exercise.  
2. 📤 **Submission:** Upload your Jupyter Notebook (`.ipynb` file) to Canvas **before the end of this week**.


---

### Please check the detail of Week 5 assignment [here](https://github.com/dangkh/COMP4010-COMP5010--Spring25/blob/master/Week5/week5_lab_assignments.docx): 

### 🚀 Submission Guidelines

📌 Ensure your Jupyter Notebook includes **all required charts and explanations**  
📂 **File Format:** `Week4_lab_assignment_YourID.ipynb`  
📤 **Upload to:** Canvas **before the deadline**.  

---

🎯 **Good luck and happy coding!** 🚀📊  

