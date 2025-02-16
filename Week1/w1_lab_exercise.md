```python
import sys
```

```python
print(sys.executable)
```

C:\Users\elhaj.m\OneDrive - VINACADEMY LLC\modules\[Spring 2025] Data Visualization\Mo\Week 1\week1_lab\venv\Scripts\python.exe

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

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

  Month  Sales  Temperature
0   Jan    200           30
1   Feb    220           32
2   Mar    250           35
3   Apr    270           40
4   May    300           42
5   Jun    320           45
```python
plt.figure(figsize=(8, 5))
sns.barplot(x='Month', y='Sales', data=df)
plt.title('Monthly Sales')
plt.show()
```

```python
plt.figure(figsize=(8, 5))
sns.lineplot(x='Month', y='Temperature', data=df, marker='o')
plt.title('Monthly Temperature')
plt.show()
```

```python
plt.figure(figsize=(8, 5))
sns.scatterplot(x='Temperature', y='Sales', data=df)
plt.title('Sales vs. Temperature')
plt.show()
```

```python
plt.figure(figsize=(8, 5))
sns.barplot(x='Month', y='Sales', data=df)
plt.ylim(200, 350)  # Truncated Y-axis
plt.title('Truncated Axis: Misleading Sales Growth')
plt.show()
```

```python
plt.figure(figsize=(8, 5))
sns.lineplot(x='Month', y='Sales', data=df, label='Sales', marker='o')
sns.lineplot(x='Month', y='Temperature', data=df, label='Temperature', marker='s')
plt.title('Overloaded Chart: Too Much Information')
plt.legend()
plt.show()
```

```python
pie_data = [30, 40, 35]
labels = ['Product A', 'Product B', 'Product C']
plt.figure(figsize=(6, 6))
plt.pie(pie_data, labels=labels, explode=(0, 0.1, 0), autopct='%1.1f%%', startangle=90)
plt.title('Misleading Pie Chart: Exaggerated Differences')
plt.show()
```

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

C:\Users\elhaj.m\AppData\Local\Temp\ipykernel_22888\593059772.py:2: FutureWarning: 

Passing `palette` without assigning `hue` is deprecated and will be removed in v0.14.0. Assign the `x` variable to `hue` and set `legend=False` for the same effect.

  sns.barplot(x='Month', y='Sales', data=df, palette='Blues_d')

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

```python
fig, ax = plt.subplots(2, 1, figsize=(10, 8))

sns.barplot(x='Month', y='Sales', data=df, ax=ax[0], palette='coolwarm')
ax[0].set_title('Monthly Sales')

sns.lineplot(x='Month', y='Temperature', data=df, marker='o', ax=ax[1], color='green')
ax[1].set_title('Monthly Temperature')

plt.tight_layout()
plt.show()
```

C:\Users\elhaj.m\AppData\Local\Temp\ipykernel_22888\2543474236.py:3: FutureWarning: 

Passing `palette` without assigning `hue` is deprecated and will be removed in v0.14.0. Assign the `x` variable to `hue` and set `legend=False` for the same effect.

  sns.barplot(x='Month', y='Sales', data=df, ax=ax[0], palette='coolwarm')

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

```python
url = 'https://covid.ourworldindata.org/data/owid-covid-data.csv'
covid_df = pd.read_csv(url)
covid_df.head()
```

  iso_code continent     location        date  total_cases  new_cases  \
0      AFG      Asia  Afghanistan  2020-01-05          0.0        0.0   
1      AFG      Asia  Afghanistan  2020-01-06          0.0        0.0   
2      AFG      Asia  Afghanistan  2020-01-07          0.0        0.0   
3      AFG      Asia  Afghanistan  2020-01-08          0.0        0.0   
4      AFG      Asia  Afghanistan  2020-01-09          0.0        0.0   

   new_cases_smoothed  total_deaths  new_deaths  new_deaths_smoothed  ...  \
0                 NaN           0.0         0.0                  NaN  ...   
1                 NaN           0.0         0.0                  NaN  ...   
2                 NaN           0.0         0.0                  NaN  ...   
3                 NaN           0.0         0.0                  NaN  ...   
4                 NaN           0.0         0.0                  NaN  ...   

   male_smokers  handwashing_facilities  hospital_beds_per_thousand  \
0           NaN                  37.746                         0.5   
1           NaN                  37.746                         0.5   
2           NaN                  37.746                         0.5   
3           NaN                  37.746                         0.5   
4           NaN                  37.746                         0.5   

   life_expectancy  human_development_index  population  \
0            64.83                    0.511    41128772   
1            64.83                    0.511    41128772   
2            64.83                    0.511    41128772   
3            64.83                    0.511    41128772   
4            64.83                    0.511    41128772   

   excess_mortality_cumulative_absolute  excess_mortality_cumulative  \
0                                   NaN                          NaN   
1                                   NaN                          NaN   
2                                   NaN                          NaN   
3                                   NaN                          NaN   
4                                   NaN                          NaN   

   excess_mortality  excess_mortality_cumulative_per_million  
0               NaN                                      NaN  
1               NaN                                      NaN  
2               NaN                                      NaN  
3               NaN                                      NaN  
4               NaN                                      NaN  

[5 rows x 67 columns]
```python
vietnam_df = covid_df[covid_df['location'] == 'Vietnam']
vietnam_df = vietnam_df[['date', 'new_cases', 'new_deaths']].dropna()
vietnam_df['date'] = pd.to_datetime(vietnam_df['date'])
vietnam_df.head()

```

             date  new_cases  new_deaths
418182 2020-01-05        0.0         0.0
418183 2020-01-06        0.0         0.0
418184 2020-01-07        0.0         0.0
418185 2020-01-08        0.0         0.0
418186 2020-01-09        0.0         0.0
```python
plt.figure(figsize=(12, 6))
sns.lineplot(data=vietnam_df, x='date', y='new_cases', color='blue')
plt.title('Daily New COVID-19 Cases in Vietnam')
plt.xlabel('Date')
plt.ylabel('New Cases')
plt.show()

```

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

