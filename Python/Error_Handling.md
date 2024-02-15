**CONTENTS**
- [Raise Error](#raise-error)
- [Error Handling (Try, except, elss, finally)](#error-handling-try-except-elss-finally)


## Raise Error 
	```python
	def func_raise(p1, p2):
		if type(p1) is not str:
			raise TypeError("that must be instance of str")
		elif p1 not in p2:
			raise ValueError("p1 not in p2")
	```

## Error Handling (Try, except, elss, finally)
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
