**CONTENTS**
- [Error Raising](#error-raising)
- [Error Handling (Try,except,elss,finally)](#error-handling-tryexceptelssfinally)


## Error Raising

```python
def colorize(text, color):
	colors = ("yellow", "blue", "green", "magenta")
	if type(text) is not str:
		raise TypeError("text must be instance of str")
	elif color not in colors:
		raise ValueError("color is invalid color")
	print(f"Printed {text} in {color}")
```

## Error Handling (Try,except,elss,finally)
```python
def divide(a,b):
 	try:
 	    result = a / b
	# catch all exceptions.	
	except: 
	    print("Something went wrong!")
	# catch the specified exception.
 	except ZeroDivisionError:
 		print("don't divide by zero please!")
 	except TypeError as err:
 		print("a and b must be ints or floats")
 		print(err)
	except (ZeroDivisionError, TypeError) as err:
		print("Something went wrong!")
		print(err)
	# extention of try bloc --> if no exception then run else bloc.
 	else:
  		print(f"{a} divided by {b} is {result}")
	finally:
		print("RUNS NO MATTER WHAT!")
```