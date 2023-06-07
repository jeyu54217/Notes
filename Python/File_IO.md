**CONTENTS**
- [General](#general)
  - [File Closing (with)](#file-closing-with)
- [TXT](#txt)
  - [open()](#open)
- [CSV](#csv)
  - [1. open() + Build-in CSV parser](#1-open--build-in-csv-parser)
  - [2. open() + Pandas (Recommend)](#2-open--pandas-recommend)
- [XML](#xml)
- [SQL DB](#sql-db)
  - [Django I/O + ORM](#django-io--orm)
    - [sqlite](#sqlite)
    - [PostgreSQL](#postgresql)
    - [MySQL](#mysql)
  - [SQL I/O](#sql-io)
    - [sqlite](#sqlite-1)
    - [PostgreSQL](#postgresql-1)
    - [MySQL](#mysql-1)
# General
## File Closing (with)
- "with" statement close file automatically. (Recommended)
- Once closed, a file can't be .read() again. (should be reopen)
- Always .close() files - it frees up system resources!
```python
# Bad code
file = open("<file.txt>")
file.read()
file.close()

file.closed # True

# ・Good code
with open("<file.txt>",) as file:
    data = file.read()

file.closed # True
```

# TXT

## open()
- "r" mode by default
- Cursor Movement : Python reads files by using a cursor
- seek() : To move the cursor.
- readlines() : To get a list of all lines.
- To read only part of a file, pass a number of characters into read("abc"), or use readline()
- "w" mode - Write to a file (previous contents will be removed)
- "a" mode - Append to a file (previous contents will not be removed)
- Write or create : You can also write to files that don't yet exist 
```python

file_path = "example.txt"

# Writting the text to a text file in write mode (previous contents will be removed)
with open(file_path, "w") as file:
    file.write("Hello, world!\n")
    file.write("This is an example file.\n")
    file.write("Writing some text to demonstrate file I/O.")

# Appending the text to a text file in append mode (previous contents will not be removed)
with open(file_path, "a") as file:
    file.write("\nAppending more text to the file.")

# Reading the text to a text file in read mode 
with open(file_path, "r") as file:
    # Read the entire file
    content = file.read()
    print(content)

```


# CSV
## 1. open() + [Build-in CSV parser](https://docs.python.org/3/library/csv.html) 
```python
import csv

file_path = "example.csv"

# Sample data
sample_data = []

# Writing to a CSV file in write mode
with open(file_path, "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(sample_data)
    
# Writing to a CSV file in append mode
with open(file_path, "a", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(sample_data)

# Reading from a CSV file in read mode
# Return List
with open(file_path, "r") as file:
    reader = csv.reader(file)
    next(reader).   # To skip the headers
    for row in reader:
        print(row)  # Each row is a list
        
# Return Dict
with open(file_path, "r") as file:
    reader = csv.DictReader(file)
    for row in reader:
        # Each row is a an OrderedDict
        # Use keys to access data
        print(row['Name'])  # Each row is a an OrderedDict

```
## 2. open() + Pandas (Recommend)
```python
import pandas as pd

file_path = "example.csv"

# Sample data (Iterable, dict)
data = {}

# Read the CSV file into a DataFrame
df = pd.read_csv(file_path)
print(df)

# Writtin/Appending the DataFrame to a CSV file
df = pd.DataFrame(data)                                   # Init a DataFrame from the targeted data
df.to_csv(file_path, index=False)                         # Write the DataFrame to a CSV file
df.to_csv(file_path, mode="a", header=False, index=False) # Appending the DataFrame to a CSV file
```
# XML
- Python pandas does not have built-in support for directly reading and writing XML files.
- parsing libraries
    1. xml.etree.ElementTree: This library is included in Python's standard library and provides a simple and efficient way to parse and manipulate XML data. It offers a high-level ElementTree API for parsing and traversing XML structures.

    2. lxml (recommended): This is a third-party library that builds upon the libxml2 and libxslt libraries. It provides a fast and feature-rich XML and HTML processing framework. It offers both a tree-based and event-based API for parsing XML data.

    3. xml.dom: This library is also part of the Python standard library and provides an implementation of the W3C's Document Object Model (DOM) for XML documents. It allows you to manipulate XML data in a tree-like structure.

    4. BeautifulSoup: While primarily used for HTML parsing, BeautifulSoup can also handle XML data. It provides a convenient and flexible way to parse and navigate XML or HTML documents. It is often used for web scraping tasks.
```python
import pandas as pd
from lxml import etree

# Reading from an XML file
file_path = "example.xml"

# Parse the XML file
tree = etree.parse(file_path)
root = tree.getroot()

# Extract data from XML and create a list of dictionaries
data = []
for element in root:
    record = {}
    for sub_element in element:
        record[sub_element.tag] = sub_element.text
    data.append(record)

# Create a DataFrame from the data
df = pd.DataFrame(data)

# Print the DataFrame
print(df)

# Writing to an XML file
# Convert DataFrame to a dictionary
data_dict = df.to_dict(orient="records")

# Create the root element
root = etree.Element("root")

# Create child elements from the DataFrame data
for record in data_dict:
    child = etree.SubElement(root, "record")
    for key, value in record.items():
        sub_element = etree.SubElement(child, key)
        sub_element.text = str(value)

# Create the XML tree
tree = etree.ElementTree(root)

# Write the XML tree to a file
output_file_path = "output.xml"
tree.write(output_file_path, pretty_print=True)


```

# SQL DB
## Django I/O + ORM
### sqlite
### PostgreSQL
### MySQL
## SQL I/O
### sqlite
  - Using Python Standard Library : [sqlite3](https://docs.python.org/3/library/sqlite3.html)
  ```python
import sqlite3

# Connect/Create the database in the current directory
conn = sqlite3.connect("db.sqlite3")

# Create a cursor object
cursor = conn.cursor()

# Execute SQL query
cursor.execute("SELECT * FROM my_table")

# Commit the transaction query (INSERT, UPDATE, DELETE, REPLACE)
conn.commit()

# Shows the result by fetchall() (return a list of tuples)
results = cursor.fetchall()
print(results)

# Close the cursor and the connection
cursor.close()
conn.close()
  ```
### PostgreSQL
### MySQL
