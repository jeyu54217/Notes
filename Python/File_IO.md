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
- "w" mode - Write to a file (previous contents removed)
- "a" mode - Append to a file (previous contents not removed)
- Write or create : You can also write to files that don't yet exist 
```python
with open("<file.txt>", "w") as file:
    file.write("test test n")
    file.write("test" * 10000)
```
## 2. Pandas (Recommended)


# CSV
## 1. open()
```python
with open("<file.csv>") as file:
    data = file.read()
```
## 2. csv
```python
from csv import reader
with open("fighters.csv") as file:
    csv_reader = reader(file)
    next(csv_reader) #To skip the headers
    for fighter in csv_reader:
    	# Each row is a list
    	# Use index to access data
    	print(f"{fighter[0]} is from {fighter[1]}") 

# Example where data is cast into a list
from csv import reader
with open("fighters.csv") as file:
    csv_reader = reader(file)
    data = list(csv_reader)
    print(data)

# Reading/Parsing CSV Using a DictReader:
from csv import DictReader
with open("fighters.csv") as file:
    csv_reader = DictReader(file)
    for row in csv_reader:
        # Each row is an OrderedDict!
        print(row['Name']) #Use keys to access data
```
## 3. Pandas (Recommended)
# EXCEL
### Pandas
# SQL DB
