## Raise Error

```python
def colorize(text, color):
	colors = ("yellow", "blue", "green", "magenta")
	if type(text) is not str:
		raise TypeError("text must be instance of str")
	elif color not in colors:
		raise ValueError("color is invalid color")
	print(f"Printed {text} in {color}")
```

## Catch Error (Try_except_elss_finally)
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
	# catch the specified exceptions.
	except (ZeroDivisionError, TypeError) as err:
		print("Something went wrong!")
		print(err)
	# extention of try bloc --> if no exception then run else bloc.
 	else:
  		print(f"{a} divided by {b} is {result}")
	finally:
		print("RUNS NO MATTER WHAT!")
```