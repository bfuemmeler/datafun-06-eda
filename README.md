# datafun-06-eda
Project 6 EDA
# Exploratory Data Analysis
# Dataset "tips" https://github.com/mwaskom/seaborn-data/commit/799924f46906146ad36b8b1c27d83e51dd8b411a
# Dataset includes "total_bill", "tip", "sex", "smoker", "day", "time", "size"

# Objective
Perform and publish a custom EDA project to demonstrate skills with Jupyter, pandas, Seaborn and popular tools for data analytics. The notebook should tell a data story and visually present findings in a clear and engaging manner.

## Initial Project Setup
## Commands Used to update GitHub- use frequently throughout

```
git add .
git commit -m "initial commit"
git push -u origin main
```
## Create & Activate Virtual Environment

```
python -m venv .venv
.venv\Scripts\activate
```
## Install Packages into requirements.txt
# copy & paste into .txt file
```
jupyterlab_widgets
pandas as pd
matplotlib.pyplot as plt
seaborn as sns

##  Type hint for Axes object (basic plot type returned by Seaborn)
# A seaborn plot is a set of axes and you can set the title, labels, etc. on the axes.

from matplotlib.axes import Axes
```
# run to install into requirements.txt
python -m pip install -r requirements.txt

# run to update into requirements.txt
python -m pip install <package_name>
```
```
# Load the dataset into a pandas DataFrame - adjust this process for your custom data
df = sns.load_dataset('tips')

# Inspect first rows of the DataFrame
print(df.head())
```
```
# Inspect histogram by numerical column
df['tip'].hist()

# Inspect histograms for all numerical columns
df.hist()

# Show all plots
plt.show()
```
```
## Begin to analyze and manipulate data

# Inspect value counts by categorical column
df['sex'].value_counts()

# Inspect value counts for all categorical columns
for col in df.select_dtypes(include=['object', 'category']).columns:
    # Display count plot
    sns.countplot(x=col, data=df)
    plt.title(f'Distribution of {col}')
    plt.show()

# Show all plots
plt.show()
```
## Add markdown fields to describe each group of graphs and how you've analyzed them.
```
## Rename column "sex" to read "gender"
df.rename(columns={'sex': 'Gender'}, inplace=True)

print(df)
```
```
## Add column for Tip % of Total Bill
# Load dataset
tips = sns.load_dataset("tips")

# Create a new column for tip percentage
tips["tip_pct"] = (tips["tip"] / tips["total_bill"]) * 100

# Display the first few rows
print(tips.head())
```
```
## Display a scatterplot
# Show the Average % vs Total Bill, looking at the dinner vs lunch shift

sns.scatterplot(x="total_bill", y="tip_pct", data=tips, hue="time")
plt.axhline(tips["tip_pct"].mean(), color="red", linestyle="--", label="Avg Tip %")
plt.legend()
plt.title("Tip Percentage vs. Total Bill")
plt.show()
```






