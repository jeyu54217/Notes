**CONTENTS**
- [General](#general)
  - [File Closing (with)](#file-closing-with)
- [TXT - open()](#txt---open)
- [CSV](#csv)
  - [1. Pandas](#1-pandas)
  - [2. Build-in CSV parser](#2-build-in-csv-parser)
- [XML](#xml)
- [SQL DB](#sql-db)
  - [Django ORM](#django-orm)
    - [Sqlite](#sqlite)
    - [MySQL](#mysql)
  - [SQL I/O](#sql-io)
    - [Sqlite](#sqlite-1)
    - [PostgreSQL](#postgresql)
    - [MySQL](#mysql-1)
- [Solutions](#solutions)
  - [- Input multiple csv files from zip to sql with buffering.](#--input-multiple-csv-files-from-zip-to-sql-with-buffering)

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
## 1. [Pandas](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html)
```bash
pip install pandas
```
```python
# pandas 2.0
import pandas as pd
import traceback

input_csv_path = "data.csv"
output_csv_path = "output.csv"
```
```python
try:
    # Reading CSV to DataFrame
    df = pd.read_csv(
        # General
        path_or_buf = input_csv_path, # expects file path or text file-like object as input.
        memory_map = False, # Build-in in-memory buffer
        engine = None, # 'c', 'python'
        encoding = 'utf-8',
        nrows = None, # Number of rows of file to read. For reading pieces of large files. (int)
        compression = None, # Only handles a single file inside a ( 'infer','zip','gzip','bz2','zstd','tar')
        # Column
        header = 'infer', # Row number(s) to use as the column names ('infer', int, [int,], None)
        index_col = None, # Column(s) to use as the row labels of the DataFrame (int, str, False) 
        names = []   # Used to rename the columns 
        usecols = None, # selected columns to be used (list)
        converters = None, # converting values in certain columns (dict)
        # Content
        sep = ',' # Delimiter ex. "|" 
        escapechar = None # "\\"
        skiprows = None, 
        na_values = None, 
        keep_default_na = True, 
        na_filter = True, 
        verbose = False, 
        skip_blank_lines = True, 
        # Date
        parse_dates = None, 
        infer_datetime_format = None, 
        keep_date_col = False, 
        date_parser = None, 
        date_format = None, 
        dayfirst = False, 
        cache_dates = True, 
        )

    # Output DataFrame here
    # ...

except FileNotFoundError:
    print("File not found when reading CSV file.")
except pd.errors.ParserError:
    print("Error parsing the CSV file.")
    print(traceback.format_exc())
except pd.errors.EmptyDataError:
    print("The CSV file is empty.")
except KeyboardInterrupt:
    print("Process interrupted by the user.")
except Exception as e:
    print("An error occurred: ", str(e))
    print(traceback.format_exc())
```

```python
# Writing DataFrame to CSV file
try:
    df.to_csv(
        path_or_buf = file_path, # If None, returns the resulting csv as a string.
        index = True, #	Write row names
        mode = 'w',
        encoding = 'utf-8', # defaults 'utf-8'
        chunksize = None, # Rows to write at a time (int)
        compression = { 
            'method': None, # 'infer', 'zip', 'gzip', 'bz2', 'zstd', 'tar'
            'compresslevel': None, # 1~9
            },
        )
    print("CSV file created successfully!")
except PermissionError:
    print("Permission denied. Unable to write the CSV file.")
```

## 2. Build-in [CSV parser](https://docs.python.org/3/library/csv.html) 
```python
import csv

file_path = "example.csv"
csv_list = []
csv_dict = {}
```
```python
# Reading CSV file (Return List)
try:
    with open(file_path, "r") as file:
        reader = csv.reader(file)
        next(reader)  # To skip the headers
        for row in reader: # Each row is a list
            csv_list.append(row)  
except FileNotFoundError:
    print("File not found.")
except Exception as e:
    print("An error occurred:", str(e))
```
```python
# Reading CSV file (Return Dict)
try:
    with open(file_path, "r") as file:
        reader = csv.DictReader(file)
        for row in reader: # Each row is an OrderedDict
            csv_dict.update(row)
except FileNotFoundError:
    print("File not found.")
except Exception as e:
    print("An error occurred:", str(e))
```
```python
# writing csv file
try:
    with open(file_path, "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerows(csv_list)
        print("CSV file created successfully!")
except Exception as e:
    print("An error occurred:", str(e))
```
```python
# appending csv file
try:
    # Writing to a CSV file in append mode
    with open(file_path, "a", newline="") as file:
        writer = csv.writer(file)
        writer.writerows(sample_data)
        print("Data appended to CSV file successfully!")
except FileNotFoundError:
    print("File not found.")
    # switch to writing mode
    # print("File not found. Creating a new file...")
    # try:
    #     with open(file_path, 'w', newline='') as file:
    #         writer = csv.writer(file)
    #         writer.writerows(data_list)
    #     print("New CSV file created and data written successfully!")
    # except Exception as e:
    #     print("An error occurred while creating the file:", str(e))
except PermissionError:
    print("Permission denied. Unable to write the CSV file.")
except Exception as e:
    print("An error occurred:", str(e))
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
- settings.py (Using OS environment variable)
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
- settings.py (Using OS environment variable)
  ```python
    import os

    DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
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
    ```
    ```python
    # sqlite I/O 
    try:
        # Connect or create the database in the current directory
        conn = sqlite3.connect("db.sqlite3")
        print("Database connection established.")
        # Create a cursor object
        cursor = conn.cursor()

        # CRUD here
        # ...

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
    ```python
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
    ```
    ```python
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
    ```
    ```python
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
    ```
    ```python
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
    ```
    ```python
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
    ```

### PostgreSQL
- Adapter : [psycopg2](https://pypi.org/project/psycopg2)
  ```bash
  pip install psycopg2
  ```
  ```python
  import psycopg2
  import traceback
  import os
  ```
  ```python
    try:
        # Connect to the PostgreSQL database
         conn = psycopg2.connect(
            host = os.environ.get('DB_HOST', 'localhost'),
            port = os.environ.get('DB_PORT', '5432'),
            database = os.environ.get('DB_NAME', '<default_value>'),
            user = os.environ.get('DB_USER', '<default_value>'),
            password = os.environ.get('DB_PASSWORD', '<default_value>'),
        )
        print("Database connection established.")

        # Create a cursor object
        cursor = conn.cursor()

        # CRUD here
        # ...

        # Commit the transaction (INSERT, UPDATE, DELETE)
        conn.commit()

    except psycopg2.Error:
        print("PostgreSQL error occurred while connecting to the database:")
        print(traceback.format_exc()) 
    finally:
        # Close the cursor and the connection
        if cursor:
            cursor.close()
            print("Cursor closed.")
        if conn:
            conn.close()
            print("PostgreSQL connection closed.")
  ```
  ```python
      # CREATE Table
      try:
          create_table_query = """
              CREATE TABLE IF NOT EXISTS my_table (
                  id SERIAL PRIMARY KEY,
                  name VARCHAR(255),
                  age INTEGER
          )
          """
          cursor.execute(create_table_query)
          print("Table created successfully")
      except psycopg2.Error as e:
          print("PostgreSQL error occurred while CREATING table:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  ```
  ```python
      # INSERT operation
      try:
          insert_query = "INSERT INTO your_table (name, age) VALUES (%s, %s)"
          data = ("John Doe", 25)
          cursor.execute(insert_query, data)
          print("Data inserted successfully")
      except psycopg2.Error as e:
          print("PostgreSQL error occurred while CREATING table:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  ```
  ```python
     # READ operation
      try:
          select_query = "SELECT * FROM your_table"
          cursor.execute(select_query)
          records = cursor.fetchall()
          for record in records:
              print(record)
      except psycopg2.Error as e:
          print("PostgreSQL error occurred while READING data:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  ```
  ```python
      # UPDATE operation
      try:
          update_query = "UPDATE your_table SET age = %s WHERE name = %s"
          data = (30, "John Doe")
          cursor.execute(update_query, data)
          print("Data Updated successfully")
      except psycopg2.Error as e:
          print("PostgreSQL error occurred while UPDATING data:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  ```
  ```python
      # DELETE operation
      try:
          delete_query = "DELETE FROM your_table WHERE name = %s"
          data = ("John Doe",)
          cursor.execute(delete_query, data)
          print("Data Deleted successfully")
      except psycopg2.Error as e:
          print("PostgreSQL error occurred while DELETING data:")
          print(traceback.format_exc())
          print("SQL Query:", e.statement)
  ```

### MySQL
- Adapter : [mysqlclient](https://pypi.org/project/mysqlclient)
```bash
pip install mysqlclient
```
```python
import MySQLdb
import traceback
import os

try:
    # Connect to the MySQL database
    connection = MySQLdb.connect(
        host = os.environ.get('DB_HOST', 'localhost'),
        user = os.environ.get('DB_USER', '<default_value>'),
        password = os.environ.get('DB_PASSWORD', '<default_value>'),
        database = os.environ.get('DB_NAME', '<default_value>'),
    )
    print("Connected to the MySQL database")
      
    # Create a cursor object
    cursor = conn.cursor()

    # CREATE Table
    try:
        create_table_query = """
            CREATE TABLE IF NOT EXISTS my_table (
                id INT AUTO_INCREMENT PRIMARY KEY,
                name VARCHAR(255),
                age INT,
              )
           """
        cursor.execute(create_table_query)
        print("Table created successfully")
    except MySQLdb.Error as e:
        print("MySQL error occurred while CREATING table:")
        print(traceback.format_exc())
        print("SQL Query:", e.statement)

    # INSERT operation
    try:
        insert_query = "INSERT INTO my_table (name, age) VALUES (%s, %s)"
        data = ("John Doe", 25)
        cursor.execute(insert_query, data)
        print("Data inserted successfully")
    except MySQLdb.Error as e:
        print("MySQL error occurred while CREATING table:")
        print(traceback.format_exc())
        print("SQL Query:", e.statement)
  
    # READ operation
    try:
        select_query = "SELECT * FROM my_table"
        cursor.execute(select_query)
        records = cursor.fetchall()
        for record in records:
            print(record)
    except MySQLdb.Error as e:
        print("MySQL error occurred while READING data:")
        print(traceback.format_exc())
        print("SQL Query:", e.statement)

    # UPDATE operation
    try:
        update_query = "UPDATE my_table SET age = %s WHERE id = %s"
        data = (30, 1)
        cursor.execute(update_query, data)
        print("Data Updated successfully")
    except MySQLdb.Error as e:
        print("MySQL error occurred while UPDATING data:")
        print(traceback.format_exc())
        print("SQL Query:", e.statement)

    # DELETE operation
    try:
        delete_query = "DELETE FROM my_table WHERE id = %s"
        data = (2,)
        cursor.execute(delete_query, data)
        print("Data Deleted successfully")
    except MySQLdb.Error as e:
        print("MySQL error occurred while DELETING data:")
        print(traceback.format_exc())
        print("SQL Query:", e.statement)

    # Commit the transaction (INSERT, UPDATE, DELETE)
    conn.commit()

  except MySQLdb.Error:
    print("MySQL error occurred while connecting to the database:")
    print(traceback.format_exc()) 

  finally:
    # Close the cursor and the connection
    if cursor:
        cursor.close()
        print("Cursor closed.")
    if conn:
        conn.close()
        print("MySQL connection closed.")
```

# Solutions
## - Input multiple csv files from zip to sql with buffering.
```python
# Input multiple csv files from zip to sql with buffering.
import pandas as pd
import zipfile 
import sqlite3 
import traceback
import os

zip_path = "examples.zip"
db_path = 'db.sqlite3'

try:
    with zipfile.ZipFile(zip_path, 'r') as zip_file: 
        # get all csv names in zip
        csv_name_list = [file for file in zip_file.namelist() if file.endswith('_lvr_land_a.csv')]
        print("Open zip file successfully!")
        # converting csv to dataframe with buffering
        try:
            data_frames = [] 
            for csv_file in csv_name_list:
                # open the csv file in binary mode as a binary file-like object on RAM (without extracting it to the disk.)
                with zip_file.open(csv_file) as buf_file: 
                    # converting a binary file-like object into a text file-like object
                    buf_str = io.TextIOWrapper(buf_file) 
                    df = pd.read_csv(buf_str) # expects a file path or a text file-like object as input.
                    data_frames.append(df)
            combined_df = pd.concat(data_frames)        
            print("CSV converting successfully!")
        except:
            print("Error occurred when converting the csv files")
            print(traceback.format_exc())
        # Insert dataframe to sql
        try:
            sql_conn = sqlite3.connect(db_path)
            combined_df.to_sql(
                name='real_estate_crawler_real_estate_raw', # Table name
                con = sql_conn,
                if_exists = 'append',
                index = False,
                )
            print("Writting dataframe to sql successfully! ")
        except:
            print("Error occurred when writting to sql")
            print(traceback.format_exc())
        finally:
            sql_conn.close()
            print("Close SQL connection successfully! ")
except:
    print("Error occurred when opening zip file")
    print(traceback.format_exc())
finally:
    os.remove(zip_path)
    print("Cleanup zip file successfully! ")

```
