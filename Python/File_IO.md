# TXT

## Close File
- Once closed, a file can't be .read() again. (should be reopen)
- Always .close() files - it frees up system resources!
- "with" statement will close file automatically.

## Read txt
- "r" mode by default
- Cursor Movement : Python reads files by using a cursor
- seek() : To move the cursor.
- readlines() : To get a list of all lines.
- To read only part of a file, pass a number of characters into read("abc"), or use readline()
```python
file = open("<file.txt>")
file.read()
file.close()

file.closed # True
```

## Write txt
- "w" mode - Write to a file (previous contents removed)
- "a" mode - Append to a file (previous contents not removed)
- Write or create : You can also write to files that don't yet exist 
```python
with open("<file.txt>", "w") as file:
    file.write("test test n")
    file.write("test" * 10000)

file.closed # True
```

# CSV

