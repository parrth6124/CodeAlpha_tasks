# 📚 Data Analyst Task 1 – Web Scraping

## 📌 Project Overview

This project is part of my **Data Analyst learning journey**.
The objective of this task is to collect book-related data from a website using **Python Web Scraping**, clean the collected data, and prepare it for further **Exploratory Data Analysis (EDA)**.

The website used for this project is **Books to Scrape**, a practice website designed for web scraping.

---

## 🎯 Objectives

* Learn the fundamentals of web scraping.
* Extract book information from multiple web pages.
* Collect approximately **1,000 book records**.
* Store the scraped data in a structured format.
* Perform basic data cleaning.
* Check data quality and identify potential issues.
* Prepare the dataset for further analysis.

---

## 🌐 Website Used

**Books to Scrape**

Website: https://books.toscrape.com/

The website contains information about books such as:

* Book Title
* Price
* Rating
* Availability
* Product information

---

## 🛠️ Technologies Used

* **Python**
* **Requests**
* **BeautifulSoup**
* **Pandas**
* **Jupyter Notebook / Google Colab**

---

## 📊 Dataset

The scraped dataset contains approximately **1,000 book records**.

### Dataset Columns

| Column         | Description           |
| -------------- | --------------------- |
| `Title`        | Name of the book      |
| `Price`        | Price of the book     |
| `Rating`       | Customer rating       |
| `Availability` | Availability status   |
| `URL`          | Book/product page URL |

---

## 🔄 Web Scraping Process

### Step 1 – Import Libraries

```python
import requests
from bs4 import BeautifulSoup
import pandas as pd
```

### Step 2 – Collect Web Pages

The website contains multiple pages of books. Python is used to send requests to each page.

```python
for page in range(1, 51):
    if page == 1:
        url = "https://books.toscrape.com/"
    else:
        url = f"https://books.toscrape.com/catalogue/page-{page}.html"
```

### Step 3 – Parse HTML

BeautifulSoup is used to read and extract information from the HTML page.

```python
response = requests.get(url)
soup = BeautifulSoup(response.text, "html.parser")
```

### Step 4 – Extract Book Information

For every book, the following information is extracted:

```python
title = book.find("h3").find("a")["title"]
price = book.find("p", class_="price_color").text
rating = book.find("p", class_="star-rating")["class"][1]
```

### Step 5 – Store Data

The extracted information is stored in a Python list and converted into a Pandas DataFrame.

```python
data.append({
    "Title": title,
    "Price": price,
    "Rating": rating
})

df = pd.DataFrame(data)
```

---

## 🧹 Data Cleaning

After scraping, the dataset is checked and cleaned.

The following checks are performed:

* Check missing values
* Check duplicate records
* Check incorrect data types
* Remove unnecessary characters from price
* Convert price into numeric format
* Check unique values
* Check inconsistent ratings
* Check overall data quality

Example:

```python
df.isnull().sum()
```

```python
df.duplicated().sum()
```

```python
df.info()
```

---

## 🔍 Data Quality Checks

The following questions are considered during data quality analysis:

1. Are there any missing values?
2. Are there duplicate books?
3. Is the price stored in the correct data type?
4. Are all ratings valid?
5. Are there any unexpected or inconsistent values?
6. Does the dataset contain approximately 1,000 records?

---

## 📈 Basic EDA Questions

After cleaning the data, the following questions can be investigated:

* What is the most expensive book?
* What is the cheapest book?
* What is the average book price?
* Which rating occurs most frequently?
* How many books are available?
* What is the price distribution?
* Which books have the highest ratings?
* Are there any duplicate records?

Example:

```python
df["Price"].max()
```

To find the title of the most expensive book:

```python
df.loc[df["Price"].idxmax(), ["Title", "Price"]]
```

---

## 📁 Project Structure

```text
Data-Analyst-Task-1/
│
├── README.md
├── web_scraping.ipynb
├── books_data.csv
└── screenshots/
```

---

## ✅ Final Outcome

By completing this task, I learned how to:

* Extract data from websites using Python.
* Work with HTML and CSS selectors.
* Use Requests and BeautifulSoup.
* Scrape data from multiple pages.
* Store scraped data in Pandas DataFrames.
* Perform basic data cleaning.
* Check data quality.
* Prepare a dataset for Exploratory Data Analysis.

Author
Parth Raval


Data Analyst / Data Science Learner

---

