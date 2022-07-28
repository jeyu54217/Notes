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

logging.debug('<msg>')       # No output 
logging.info(('<msg>')       # No output

logging.warning(('<msg>')   # WARNING:root:warning message
logging.error(('<msg>')     # ERROR:root:error message
logging.critical(('<msg>')  # CRITICAL:root:critical message
```
 ## Changing Output basicConfig
 ```python
logging.basicConfig(level = logging.DEBUG, )  # Changing default output from 'debug'
 ```

 ## Output formation
  ```python
import logging
# Default : WARNING:root:msg

FORMAT = '%(asctime)s %(levelname)s: %(message)s'
DATE_FORMAT = '%Y%m%d %H:%M:%S'  # refer to "time.strftime()"
logging.basicConfig(level = logging.<DEBUG>, format = FORMAT, datefmt = DATE_FORMAT)

%(levelname)s	# Rank name
%(name)s	    # logger name
%(message)s	    # msg

%(asctime)s	    # date time : YYYY-MM-DD HH:mm:SS,ms
%(filename)s	# file name
%(funcName)s	
%(module)s	    # module name
%(pathname)s	# file's path

%(levelno)s	    # Rank Non
%(lineno)d	    # call logger line nonmer

%(process)d 	# process ID 
%(thread)d	    # thread ID
%(threradName)s	# threradName
 ```
