## Ranking
```python
import logging
print(
    logging.NOTSET,   # 0
    logging.DEBUG,    # 10
    logging.INFO,     # 20
    
    logging.WARNING,  # 30  -- default rank, only output msg below from here.
    logging.ERROR,    # 40
    logging.CRITICAL, # 50
    )

```
## Output methods
```python
import logging

logging.debug('debug message')       # No output 
logging.info('info message')         # No output

logging.warning('warning message')   # WARNING:root:warning message
logging.error('error message')       # ERROR:root:error message
logging.critical('critical message') # CRITICAL:root:critical message
```
 ## Changing Output basicConfig
 ```python
logging.basicConfig(level = logging.DEBUG, )  # Changing default output from 'debug'
 ```

 ## Output formation
  ```python
# Default : WARNING:root:msg
%(levelname)s	# Rank name
%(name)s	    # logger name
%(message)s	    # msg

%(asctime)s	    # date time : YYYY-MM-DD HH:mm:SS,ms
%(filename)s	# file name
%(funcName)s	
%(module)s	    # module name
%(pathname)s	# file's path

%(levelno)s	# Rank Non
%(lineno)d	# call logger line nonmer

%(process)d	process ID 
%(thread)d	thread ID
%(threradName)s	threradName
 ```
