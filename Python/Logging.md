## Logging Rank 
```python
import logging
print(
    logging.NOTSET,   # 0
    logging.DEBUG,    # 10
    logging.INFO,     # 20
    
    logging.WARNING,  # 30  -- default rank, only output msg below here.
    logging.ERROR,    # 40
    logging.CRITICAL, # 50
    )

```
## Logging Output methods
```python
import logging

logging.debug('<msg>')       # No output 
logging.info(('<msg>')       # No output

logging.warning(('<msg>')   # WARNING:root:warning message
logging.error(('<msg>')     # ERROR:root:error message
logging.critical(('<msg>')  # CRITICAL:root:critical message

```
## Basic Output Config & Formation
  ```python
import logging

# Setting basic output method config
logging.basicConfig(level = logging.DEBUG)  # Default : WARNING:root:msg

# Changing basic Output FORMAT
FORMAT = '%(asctime)s %(levelname)s: %(message)s'
DATE_FORMAT = '%Y%m%d %H:%M:%S'  # refer to "time.strftime()"
logging.basicConfig(level = logging.<DEBUG>, format = FORMAT, datefmt = DATE_FORMAT)
 ```
 
 ### Output Formation
  ```python

%(levelname)s	  # Rank level name
%(name)s	      # logger name
%(message)s	   

%(asctime)s	    # date time : YYYY-MM-DD HH:mm:SS,ms
%(filename)s	  
%(funcName)s	
%(module)s	    # module name
%(pathname)s	  

%(levelno)s	    # Rank Non
%(lineno)d	    # call logger line nonmer

%(process)d 	  # process ID 
%(thread)d	    # thread ID
%(threradName)s	
 ```
