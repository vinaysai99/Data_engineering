# Day 2: Working with DataFrames I

Welcome to Day 2 of the PySpark learning journey! Today focuses on creating DataFrames and performing basic operations like selecting, filtering, and counting.

---

## 🎯 Learning Objectives

- Create DataFrames from different sources  
- Perform basic DataFrame operations (`show`, `select`, `filter`)  
- Understand DataFrame structure and properties  

---

## 📁 1. Creating DataFrames

### ✅ From Python Collections

```python
from pyspark.sql import SparkSession

# Create a SparkSession
spark = SparkSession.builder \
    .appName("Day2Learning") \
    .master("local[*]") \
    .getOrCreate()

# Create a DataFrame from a list of tuples
data = [
    ("John", "Sales", 3000),
    ("Lisa", "Marketing", 4500),
    ("Mike", "Engineering", 5000),
    ("Sarah", "Sales", 3500),
    ("Alex", "Engineering", 4800)
]

# Define schema
columns = ["Name", "Department", "Salary"]

# Create DataFrame
employees_df = spark.createDataFrame(data, columns)

# Display the DataFrame
employees_df.show()
```

### ✅ From External Sources

```python
# Create a DataFrame from a CSV file
# (Make sure to replace with actual file path)

csv_df = spark.read.csv("path/to/your/file.csv", header=True, inferSchema=True)

# Create a DataFrame from a JSON file
# json_df = spark.read.json("path/to/your/file.json")
```

## 🛠 2. Basic DataFrame Operations - Analysis
### 🔍 Viewing Data

```python
# Show contents of the DataFrame
employees_df.show()

# Show 10 rows without truncation
employees_df.show(n=10, truncate=False)

# View schema
employees_df.printSchema()

# Summary statistics
employees_df.describe().show()

# Get column names and data types
employees_df.columns
employees_df.dtypes
```

### 🎯 Selecting Data

```python
# Select specific columns
employees_df.select("Name", "Salary").show()

# Using column functions
from pyspark.sql.functions import col
employees_df.select(col("Name"), col("Salary")).show()

# Dot notation
employees_df.select(employees_df.Name, employees_df.Salary).show()
```

### 🔎 Filtering Data

```python
# Simple condition
employees_df.filter(employees_df.Salary > 4000).show()

# SQL-style condition
employees_df.filter("Salary > 4000").show()

# Multiple conditions
employees_df.filter((employees_df.Salary > 3500) & 
                    (employees_df.Department == "Engineering")).show()

```

### 📊 Counting and Distinct Values

```python
# Total number of rows
print("Total employees:", employees_df.count())

# Count of unique departments
print("Number of departments:", employees_df.select("Department").distinct().count())

# Show unique departments
employees_df.select("Department").distinct().show()

```


## 📚 Resources
- [PySpark DataFrame Documentation](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/dataframe.html)  
- [PySpark Column Documentation](https://spark.apache.org/docs/latest/api/python/reference/pyspark.sql/column.html)
