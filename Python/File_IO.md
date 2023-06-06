**CONTENTS**
- [TXT](#txt)
  - [1. open()](#1-open)
    - [Close File](#close-file)
      - [・Bad code](#bad-code)
      - [・Good code](#good-code)
    - [Read txt](#read-txt)
    - [Write txt](#write-txt)
  - [2. Pandas (Recommended)](#2-pandas-recommended)
- [CSV](#csv)
  - [1. open()](#1-open-1)
  - [2. csv](#2-csv)
  - [3. Pandas (Recommended)](#3-pandas-recommended)
- [EXCEL](#excel)
    - [Pandas](#pandas)
- [SQL DB](#sql-db)

# TXT
## 1. open()
### Close File
- "with" statement close file automatically. (Recommended)
- Once closed, a file can't be .read() again. (should be reopen)
- Always .close() files - it frees up system resources!
#### ・Bad code
```python
file = open("<file.txt>")
file.read()
file.close()

file.closed # True
```
#### ・Good code
```python
with open("<file.txt>",) as file:
    data = file.read()

file.closed # True
```

### Read txt
- "r" mode by default
- Cursor Movement : Python reads files by using a cursor
- seek() : To move the cursor.
- readlines() : To get a list of all lines.
- To read only part of a file, pass a number of characters into read("abc"), or use readline()

### Write txt
- "w" mode - Write to a file (previous contents will be removed)
- "a" mode - Append to a file (previous contents will not be removed)
- Write or create : You can also write to files that don't yet exist 
```python

file_path = "example.txt"

# Writting to a text file
# Open the file in write mode (previous contents will be removed)
with open(file_path, "w") as file:
    file.write("Hello, world!\n")
    file.write("This is an example file.\n")
    file.write("Writing some text to demonstrate file I/O.")
    
# Appending to a text file 
# Open the file in append mode (previous contents will not be removed)
with open(file_path, "a") as file:
    file.write("\nAppending more text to the file.")
    
# Reading from a text file
# Open the file in read mode
with open(file_path, "r") as file:
    # Read the entire file
    content = file.read()
    print(content)



# Reading from the text file again to see the changes
with open(file_path, "r") as file:
    content = file.read()
    print(content)

```
## 2. Pandas (Recommended)


# CSV [https://docs.python.org/3/library/csv.html]

```python
import csv

file_path = "example.csv"

# Sample data
sample_data = [
    ["Name", "Age", "City"],
    ["Alice", 25, "New York"],
    ["Bob", 30, "London"],
    ["Charlie", 35, "Paris"]
]

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
## 3. Pandas (Recommended)
# EXCEL
### Pandas
# SQL DB
