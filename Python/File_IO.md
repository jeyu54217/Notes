**CONTENTS**
- [General](#general)
  - [File Closing (with)](#file-closing-with)
- [TXT - open()](#txt---open)
- [CSV](#csv)
  - [1. Build-in CSV parser](#1-build-in-csv-parser)
  - [2. Pandas (Recommend)](#2-pandas-recommend)
- [XML](#xml)
- [SQL DB](#sql-db)
  - [Django ORM](#django-orm)
    - [Sqlite](#sqlite)
    - [MySQL](#mysql)
  - [SQL I/O](#sql-io)
    - [Sqlite](#sqlite-1)
    - [PostgreSQL](#postgresql)
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

# TXT - open()
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
## 1. Build-in [CSV parser](https://docs.python.org/3/library/csv.html) 
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
## 2. Pandas (Recommend)
```bash
pip install pandas
```
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
## Django ORM
### Sqlite
- DBMS as a single file (No adapter needed)
- settings.py
   ```python
    from pathlib import Path
    BASE_DIR = Path(__file__).resolve().parent.parent

    DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.sqlite3',
          'NAME': BASE_DIR / 'db.sqlite3',
          }
    }
    ```
### PostgreSQL
- Adapter : [psycopg2-binary](https://pypi.org/project/psycopg2-binary/) (optimized for Django usage)
  ```bash
  pip install psycopg2-binary
  ```
- settings.py (Usiing OS environment variable)
    ```python
    import os

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': os.environ.get('DB_NAME', '<default_value>'),
            'USER': os.environ.get('DB_USER', '<default_value>'),
            'PASSWORD': os.environ.get('DB_PASSWORD', '<default_value>'),
            'HOST': os.environ.get('DB_HOST', 'localhost'),
            'PORT': os.environ.get('DB_PORT', '5432'),
        }
    }
     ```
### MySQL
- Adapter : [mysqlclient](https://pypi.org/project/mysqlclient/) (optimized for Django usage)
  ```bash
  pip install mysqlclient
  ```
- settings.py (Usiing OS environment variable)
    ```python
    import os

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.postgresql',
            'NAME': os.environ.get('DB_NAME', '<default_value>'),
            'USER': os.environ.get('DB_USER', '<default_value>'),
            'PASSWORD': os.environ.get('DB_PASSWORD', '<default_value>'),
            'HOST': os.environ.get('DB_HOST', 'localhost'),
            'PORT': os.environ.get('DB_PORT', '3306'),
        }
    }
     ```
## SQL I/O
### Sqlite
  - Using Python Standard Library : [sqlite3](https://docs.python.org/3/library/sqlite3.html)
  ```python
  import sqlite3
  import traceback
  
  try:
      # Connect or create the database in the current directory
      conn = sqlite3.connect("db.sqlite3")
      print("Database connection established.")
  
      # Create a cursor object
      cursor = conn.cursor()
  
      # Create a table
      try:
          create_table_query = """
              CREATE TABLE IF NOT EXISTS my_table (
              id INTEGER PRIMARY KEY AUTOINCREMENT,
              name TEXT,
              age INTEGER
          )
          """
          cursor.execute(create_table_query)
          print("Table created successfully")
      except sqlite3.Error as e:
          print("SQLite error occurred while CREATING table:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  
      # Insert a record
      try:
          insert_query = "INSERT INTO my_table (name, age) VALUES (?, ?)"
          data = ("John Doe", 25)
          cursor.execute(insert_query, data)
         # Execute the bulk insert
          cursor.executemany(insert_query, data)
          print("Data Inserted successfully")
      except sqlite3.Error as e:
          print("SQLite error occurred while INSERTING data:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  
      # Update a record
      try:
          update_query = "UPDATE my_table SET age = ? WHERE name = ?"
          data = (30, "John Doe")
          cursor.execute(update_query, data)
          print("Data Updated successfully")
      except sqlite3.Error as e:
          print("SQLite error occurred while UPDATING data:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  
      # Delete a record
      try:
          delete_query = "DELETE FROM my_table WHERE name = ?"
          data = ("John Doe",)
          cursor.execute(delete_query, data)
          print("Data Deleted successfully")
      except sqlite3.Error as e:
          print("SQLite error occurred while DELETING data:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  
      # Read records
      try:
          select_query = "SELECT * FROM my_table"
          cursor.execute(select_query)
          records = cursor.fetchall()
          for record in records:
              print(record)
      except sqlite3.Error as e:
          print("SQLite error occurred while READING data:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  
      # Commit the transaction (INSERT, UPDATE, DELETE)
      conn.commit()
  
  except sqlite3.Error:
      print("SQLite error occurred while connecting to the database:")
      print(traceback.format_exc()) 
  
  finally:
      # Close the cursor and the connection
      if cursor:
          cursor.close()
          print("Cursor closed.")
      if conn:
          conn.close()
          print("SQLite connection closed.")
```
### PostgreSQL
- Adapter : [psycopg2](https://pypi.org/project/psycopg2)
  ```bash
  pip install psycopg2
  ```
  ```python
  import psycopg2
  from psycopg2 import Error
  import os


  ```
### MySQL
