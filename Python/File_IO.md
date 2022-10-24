

## Read txt
- Once closed, a file can't be read again
- Always close files - it frees up system resources!
```python
file = open("<file.txt>")
file.read()
file.close()

file.closed # True
```

## Write txt

- Firstly open it in "w" mode,
- You can also write to files that don't yet exist

```python
with open("<file.txt>", "w") as file:
    file.write("test test n")
    file.write("test" * 10000)

file.closed # True
```