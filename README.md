

# 🧮 RFM Analysis — Print Shop Customers

## 📘 Overview

This project performs **RFM (Recency, Frequency, Monetary) Analysis** on a dataset of **print shop customer orders** to identify the most valuable customers and those who may need re-engagement.

👉 The goal is to group customers based on how **recently**, **frequently**, and **spendingly** they purchase — helping businesses focus on customer retention and loyalty.

---

## 🧩 Project Summary

| Step                         | Description                                                               | Tool Used |
| ---------------------------- | ------------------------------------------------------------------------- | --------- |
| **1. Data Creation**         | A synthetic dataset of 1,000+ print shop orders was created using Python. | 🐍 Python |
| **2. RFM Analysis**          | R, F, and M values were calculated using Excel formulas.                  | 📊 Excel  |
| **3. Customer Segmentation** | Customers were categorized into RFM groups (Best, Loyal, At Risk, etc.).  | 📊 Excel  |

👉 In short: **Python only creates the dataset**, while **Excel performs the full RFM analysis and segmentation**.

---

## 📂 Project Files

| File                            | Description                                                        |
| ------------------------------- | ------------------------------------------------------------------ |
| `print_shop_orders.csv`         | Dataset of 1,000+ print shop orders (created in Python).           |
| `rfm_analysis.ipynb`            | Jupyter Notebook used to generate the dataset.                     |
| `print_shop_orders_result.xlsx` | Excel file containing the RFM scoring and customer segmentation.   |
| `prompt_and_formulas.docx`      | Reference document with the RFM Excel formulas and project prompt. |

---

## 🧠 What Is RFM Analysis?

**RFM** is a marketing technique that evaluates customer behavior using:

* **Recency:** How recently a customer made a purchase.
* **Frequency:** How often they purchased.
* **Monetary:** How much money they spent.

Each factor is scored on a **1–5 scale**, then combined into a total **RFM Score (out of 15)**.

---

## 🐍 Python Code — Create the Dataset

Here’s a small example of how the dataset was generated in Python before being analyzed in Excel:

```python
import pandas as pd
import numpy as np
from datetime import datetime, timedelta
import random

# Set seed for reproducibility
np.random.seed(42)
random.seed(42)

# Define parameters
num_rows = 1000
customer_ids = [f'CUST{str(i).zfill(4)}' for i in range(1, 301)]  # 300 unique customers
product_types = ['Poster', 'Canvas Print', 'Photo Book', 'Greeting Card', 'Flyer', 'Business Card']
start_date = datetime.now() - timedelta(days=365)  # last 1 year

# Generate data
order_dates = [start_date + timedelta(days=np.random.randint(0, 365)) for _ in range(num_rows)]
customer_choices = np.random.choice(customer_ids, num_rows)
products_purchased = np.random.choice(product_types, num_rows)

# Monetary values by product type, with randomness
price_dict = {
    'Poster': 15.0,
    'Canvas Print': 40.0,
    'Photo Book': 25.0,
    'Greeting Card': 5.0,
    'Flyer': 10.0,
    'Business Card': 12.0
}

monetary_values = [round(price_dict[prod] * np.random.uniform(0.8, 1.2), 2) for prod in products_purchased]

# Create dataframe
orders_df = pd.DataFrame({
    'OrderID': [f'ORDER{str(i).zfill(5)}' for i in range(1, num_rows + 1)],
    'CustomerID': customer_choices,
    'OrderDate': order_dates,
    'ProductType': products_purchased,
    'OrderValue': monetary_values
})

# Save to CSV
csv_filename = 'print_shop_orders.csv'
orders_df.to_csv(csv_filename, index=False)


This code creates:

* 1,000 random orders
* 300+ customers
* Six product categories with varied pricing
* A CSV file (print_shop_orders.csv) for Excel analysis
```
---

## 🏷️ Customer Segmentation

| Category                      | Description                              |
| ----------------------------- | ---------------------------------------- |
| **Best Customers**            | Buy recently, often, and spend the most. |
| **Loyal Customers**           | Regular buyers with consistent spending. |
| **Potential Loyal Customers** | Moderate buyers showing engagement.      |
| **Need Attention**            | Inactive or low-spend customers.         |
| **At Risk**                   | Haven’t purchased in a long time.        |

---

## 📈 Results

The Excel file `print_shop_orders_result.xlsx` includes:

* Recency, Frequency, and Monetary values
* R, F, and M scores (1–5 scale)
* Total RFM score (out of 15)
* Final customer category

---

## 🚀 How to Use

1. Open **`print_shop_orders_result.xlsx`** to explore customer segments.
2. (Optional) Run **`rfm_analysis.ipynb`** in Jupyter Notebook to recreate the dataset.
3. Filter or visualize your segments in Excel or Power BI.

---

## 💡 Key Takeaway

This project shows how to:

* Use **Python** to generate realistic business data.
* Use **Excel** to perform professional-level **RFM segmentation**.
* Quickly identify your **best**, **loyal**, and **at-risk** customers.

---



