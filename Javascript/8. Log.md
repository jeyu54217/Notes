**CONTENTS**
- [Logging](#logging)
  - [Loggers](#loggers)
  - [Handlers](#handlers)
  - [Levels](#levels)
  - [Formatters](#formatters)
  - [Example](#example)
# Logging 

Python's `logging` module offers a standardized way to log messages in your application. It can be used to report error messages, informational messages, and debug messages. Unlike using `print` statements, logging allows you to categorize messages by importance and decide the output level.



## Loggers
The entry point of the logging system. You can create different loggers to handle different parts of your application. Each logger can have different handlers and severity levels.

## Handlers
Handlers send the log records (created by loggers) to the appropriate destination. Common destinations include the console, files, email, web servers, or other outputs. You can configure multiple handlers for the same logger.

## Levels
Logging has several predefined levels indicating the severity of an event. The standard levels provided are: DEBUG, INFO, WARNING, ERROR, and CRITICAL, in increasing order of severity. This allows you to filter out less severe messages and focus on critical issues.

## Formatters
Formatters specify the layout of log records in the final output. You can include information like timestamp, logger name, and the actual message. This customization helps in parsing log files and troubleshooting.

## Example

You can configure logging by calling `logging.basicConfig(**kwargs)` with various keyword arguments to set the level, format, and destination of the log messages.

```python
import logging

logging.basicConfig(level=logging.INFO, format='%(asctime)s - %(name)s - %(levelname)s - %(message)s')
logging.info("This is an info message")


logger = logging.getLogger('example_logger')
logger.setLevel(logging.DEBUG)

# Create a file handler
handler = logging.FileHandler('example.log')
handler.setLevel(logging.DEBUG)

# Create a formatter and set it for the handler
formatter = logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s')
handler.setFormatter(formatter)

# Add the handler to the logger
logger.addHandler(handler)

logger.info('This is an info message')

```
