

## Read txt
- "r" mode is the default
- Cursor Movement : Python reads files by using a cursor
- To move the cursor, use the seek() method
- To read only part of a file, pass a number of characters into read, or use readline()
- To get a list of all lines, use readlines()
```python
file = open("<file.txt>")
file.read()
file.close()

file.closed # True
```

## Write txt
- "w" mode - Write to a file (previous contents removed)
- "a" mode - Append to a file (previous contents not removed)
- You can also write to files that don't yet exist (like update or create)
```python
with open("<file.txt>", "w") as file:
    file.write("test test n")
    file.write("test" * 10000)

file.closed # True
```

## Close File
- Once closed, a file can't be .read() again.
- Always .close() files - it frees up system resources!
- "with" statement will close file automatically.