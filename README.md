# CodeAlpha_Task-1(EDA) 
A Python-based Exploratory Data Analysis (EDA) project on a Retail Sales dataset using Pandas, NumPy, Matplotlib, and Seaborn to analyze customer behavior, sales trends, product performance, and generate meaningful business insights through data visualization.
# 🛍️ Retail Sales Data Analysis using Python

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on a Retail Sales dataset using **Python**. The objective is to analyze customer purchasing behavior, sales trends, product performance, and business insights using statistical analysis and data visualization.

---

## 🛠️ Technologies Used

- Python 3.x
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab / Jupyter Notebook

---

## 📂 Dataset

The dataset contains retail transaction information such as:

- Transaction ID
- Customer ID
- Age
- Gender
- Product Category
- Quantity
- Price per Unit
- Total Amount

---

# 📊 Analysis Steps

## 1️⃣ Import Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_style("whitegrid")
```

---

## 2️⃣ Load Dataset

```python
file = pd.read_csv('/content/retail_sales_dataset.csv')
file.head()
```

---

## 3️⃣ Dataset Overview

```python
print(file.shape)
print(file.info())
print(file.columns)
print(file.describe())
```

---

## 4️⃣ Data Cleaning

```python
print(file.isnull().sum())

print(file.duplicated().sum())

file.drop_duplicates(inplace=True)
```

---

## 5️⃣ Data Type Analysis

```python
print(file.dtypes)

file.select_dtypes(include='object').columns
```

---

## 6️⃣ Descriptive Statistics

```python
print("Average Age:", file['Age'].mean())
print("Median Age:", file['Age'].median())
print("Minimum Age:", file['Age'].min())
print("Maximum Age:", file['Age'].max())
```

---

# 📈 Charts & Visualizations

## 7️⃣ Customer Age Distribution

### Code

```python
plt.figure(figsize=(8,5))

sns.histplot(file['Age'], bins=20, kde=True)

plt.title("Customer Age Distribution")
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.show()
```

### Output

> 📷 
![image alt](https://github.com/jena92856-ops/CodeAlpha_Task-1-EDA-/blob/c7bbdede6c56bc3f0525dbde1e307a7dc8faba65/01_age_distribution.png) 
```
The age distribution is fairly even across 18–64 years, with a slight concentration in the 30–50 range.  
This shows the store serves a broad, middle-aged customer base rather than one narrow age segment.
```

---

## 8️⃣ Gender Distribution

### Code

```python
plt.figure(figsize=(6,4))

sns.countplot(x='Gender', data=file)

plt.title("Gender Distribution")

plt.show()
```

### Output

> 📷 ![image alt](

```
images/gender_distribution.png
```

---

## 9️⃣ Sales by Gender

### Code

```python
gender_sales = file.groupby('Gender')['Total Amount'].sum()

plt.figure(figsize=(7,5))

gender_sales.plot(kind='bar')

plt.title("Sales by Gender")

plt.xlabel("Gender")
plt.ylabel("Total Sales")

plt.show()
```

### Output

> 📷 Add Screenshot

```
images/sales_by_gender.png
```

---

## 🔟 Product Category Distribution

### Code

```python
plt.figure(figsize=(8,5))

sns.countplot(
    x='Product Category',
    data=file
)

plt.title("Product Category Distribution")

plt.show()
```

### Output

> 📷 Add Screenshot

```
images/product_category_distribution.png
```

---

## 1️⃣1️⃣ Revenue by Product Category

### Code

```python
category_revenue = file.groupby(
    'Product Category'
)['Total Amount'].sum().sort_values()

plt.figure(figsize=(10,6))

category_revenue.plot(kind='bar')

plt.title("Revenue by Product Category")

plt.xlabel("Product Category")
plt.ylabel("Revenue")

plt.show()
```

### Output

> 📷 Add Screenshot

```
images/revenue_by_category.png
```

---

## 1️⃣2️⃣ Total Revenue

### Code

```python
total_revenue = file['Total Amount'].sum()

print("Total Revenue Generated:", total_revenue)
```

---

## 1️⃣3️⃣ Average Transaction Value

### Code

```python
average_transaction = file['Total Amount'].mean()

print("Average Transaction Value:", average_transaction)
```

---

## 1️⃣4️⃣ Top 10 Highest Transactions

### Code

```python
top_transactions = file.sort_values(
    by='Total Amount',
    ascending=False
).head(10)

plt.figure(figsize=(10,5))

plt.bar(
    top_transactions['Transaction ID'].astype(str),
    top_transactions['Total Amount']
)

plt.xticks(rotation=45)

plt.title("Top 10 Highest Transactions")

plt.show()
```

### Output

> 📷 Add Screenshot

```
images/top_10_transactions.png
```

---

## 1️⃣5️⃣ Quantity vs Total Amount

### Code

```python
plt.figure(figsize=(8,5))

sns.scatterplot(
    x='Quantity',
    y='Total Amount',
    data=file
)

plt.title("Quantity vs Total Amount")

plt.show()
```

### Output

> 📷 Add Screenshot

```
images/quantity_vs_amount.png
```

---

## 1️⃣6️⃣ Outlier Detection

### Code

```python
plt.figure(figsize=(8,5))

sns.boxplot(
    y=file['Total Amount']
)

plt.title("Outlier Detection in Total Amount")

plt.show()
```

### Output

> 📷 Add Screenshot

```
images/outlier_detection.png
```

---

## 1️⃣7️⃣ Correlation Heatmap

### Code

```python
plt.figure(figsize=(8,6))

correlation = file.corr(numeric_only=True)

sns.heatmap(
    correlation,
    annot=True,
    cmap='coolwarm'
)

plt.title("Correlation Heatmap")

plt.show()
```

### Output

> 📷 Add Screenshot

```
images/correlation_heatmap.png
```

---

# 📈 Visualizations Included

- 📊 Customer Age Distribution
- 👨‍👩‍👧 Gender Distribution
- 💰 Sales by Gender
- 📦 Product Category Distribution
- 📈 Revenue by Product Category
- 🏆 Top 10 Highest Transactions
- 📉 Quantity vs Total Amount
- 📦 Outlier Detection (Box Plot)
- 🔥 Correlation Heatmap

---

# 📌 Key Insights

- Identified customer age distribution patterns.
- Compared sales generated by male and female customers.
- Found the highest revenue-generating product categories.
- Calculated total revenue and average transaction value.
- Identified the top 10 highest-value transactions.
- Analyzed the relationship between purchase quantity and total sales.
- Detected outliers in transaction amounts.
- Studied correlations among numerical features.

---

# 🚀 Conclusion

This project demonstrates the power of **Exploratory Data Analysis (EDA)** in extracting meaningful business insights from retail sales data. By leveraging **Python, Pandas, Matplotlib, and Seaborn**, various trends, customer behaviors, and sales patterns were uncovered, enabling data-driven business decisions.

---

## 👨‍💻 Author

**Aditya Jena**

**B.Tech (Information Technology)**

### Skills

- Python
- Data Analytics
- Machine Learning
- SQL
- Git & GitHub
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab
