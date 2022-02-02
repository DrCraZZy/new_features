# Logging

## <u>loguru</u>

```python
from loguru import logger

# log to file
logger.add(
    path_to_logfile, 
    format="{time} {level} {message}", 
    level=log_from_level,
    rotation="10 KB",  # logfile size
    compression="zip",  # compression of logfile 
    serialize=True  # write log as json
)

# log to terminal
logger.debug(message)
logger.info(message)
logger.error(message)


# Example
def divide(a,b):
    return a/b

@logger.catch  # logs data in terminal and in file
def main():
    divide(2/0)

main()
```