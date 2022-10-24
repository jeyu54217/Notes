## Logging Levels 
```python
import logging

    logging.NOTSET,   # 0   -- To print or send all the different levels to the root logger. (default)
    logging.DEBUG,    # 10  -- To provide more information and help in diagnosing the problems for other people working on the same applicati
    logging.INFO,     # 20  -- To confirms things are working as expected

    # That will be logged automatically below.
    logging.WARNING,  # 30  --  for alerting developers something unexpected is happening, has happened, or may happen. This doesn’t necessarily mean a negative action occurred, but it does require attention. 
    logging.ERROR,    # 40    when things are starting to go south. Something has gone wrong and needs immediate attention, but the error can still be resolved. Examples include an API reporting the incorrect info. 
    logging.CRITICAL, # 50  should only be used when something drastic is wrong. This is the highest level of alert and requires absolute immediate attention, as the issue may not be resolvable. For instance, the application becomes entirely unusable.


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
https://pymotw.com/3/logging/
https://docs.python.org/3/library/logging.html