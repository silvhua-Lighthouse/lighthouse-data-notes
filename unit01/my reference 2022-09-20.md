
# Table of Contents
* [Sets](#sets)
* [Copy Objects](#copy-objects)
* [Date Time](#date-and-time)
* [APIs](#apis)

## Sets
* [Reference: Real Python](https://realpython.com/python-sets/)

**See reference link for more methods**

Task | Operator | Method
--- | --- | ---
union (join) | `x1 \| x2` |  `x1.union(x2)`
intersection (common elements)    |   `x1 & x2` |   `x1.intersection(x2)`   |   `x1 \|= x2` |   `x1.update(x2,x3)`
difference  |    `x1 - x2`  |   `x1.difference(x2)`
symmetric difference (elements that are in one set but not both)    |   `x1 ^ x2`   |   `x1.symmetric_difference(x2)` *(only 1 argument allowed)*
boolean: `True` if no elements in common    |  (none) |   `x1.isdisjoint(x2)`
determine if a set is a subset of another set  |   `x1 <= x2`  |   `x1.issubset(x2)`
determine if a set is a proper subset (a subset that is non-identical) of another set   |  `x1 < x2`    |   (none) 
determine if a set is a superset (contains all elements) of another set |    `x1 >= x2` | `x1.issuperset(x2)`
is proper superset? |   `x1 > x2`   |   (none)
**Augmented Assignment**
modify a set by union   |   `x1 \|= x2` |   `x1.update(x2)`
modify a set by intersection, i.e. retain only elements found in all sets   |   `x1 &= x2`  | `x1.intersection_update(x2)`
modify by difference, i.e. remove elements found in x2  | `x1 -= x2`    |   `x1.difference_update(x2)
modify by symmetric difference, i.e. retain eelements found in either set, but not both | `x1 ^= x2`    | `x1.symmetric_difference_update(x2)`

## Copy Objects
[Reference: Python Shallow Copy and Deep Copy (With Examples) (programiz.com)](https://www.programiz.com/python-programming/shallow-deep-copy)
### Copy using `=` operator
```
oldlist = newlist
```

Changes to either variable will be visible in both because they point to the same object.
### Copy module
```python
import copy
```
Type of copy module | Description | Method
--- | --- | ---
shallow copy[^1] | Creates a new object with references to the original elements. Any changes to original elements are reflected in both lists. New elements to the old list do not get copied to the new list. | `new_list = copy.copy(old_list)`
deep copy | Creates a new object. Changes to elements in one list are not reflected in the other list. | `new_list = copy.deepcopy(old_list)`

[^1]: Shallow copy is not possible for immutable objects like integers or tuples.


## Date and Time
1. [Reference: Python Datetime Tutorial: Manipulate Times, Dates, and Time Spans (dataquest.io)](https://www.dataquest.io/blog/python-datetime-tutorial/)
2. [Reference: Python datetime (With Examples) (programiz.com)](https://www.programiz.com/python-programming/datetime)

### `datetime` Objects
```python
from datetime import datetime

# Create a datetime object for current moment
datetime_object = datetime.now() 

# Create a date object from a string in a given time format
my_string = '2019-10-31'
my_date = datetime.strptime(my_string, "%Y-%m-%d")

# create date with year, month, day, hour, minute, and second
date1 = datetime(2017, 6, 21, 18, 25, 30)
```

* `strptime()` converts string to datetime object 
* `strftime()` converts datetime objects back into strings.

Format arguments (use quotes):
* `%Y` - year [0001,..., 2018, 2019,..., 9999]
* `%m` - numerical month [01, 02, ..., 11, 12]
* `%B` - full name of month (e.g. January)
* `%b` - short name of the month (first 3 characters) [Jan, Feb]
* `%d` - day [01, 02, ..., 30, 31]
* `%H` - hour in 24-h format [00, 01, ..., 22, 23]
* `%I` - hour in 12-h format
* `%M` - minute [00, 01, ..., 58, 59]
* `%S` - second [00, 01, ..., 58, 59]
* `%p` - time in AM/PM
* `%j` - day of the year

`datetime` class attributes:
* `my_date.year` Gets the year from the date
* `my_date.month` Gets the month
* `my_date.day` Gets the day of the month
* `my_date.hour`
* `my_date.minute`
* `my_date.strftime(<format>)`

### `date` object 
```python
from datetime import date
date1 = date(2008, 8, 18)

datetoday = date.today()
```
`date` object attributes are similar as for `datetime`

### `time` object
```Python
from datetime import time
# time(hour, minute and second)
b = time(11, 34, 56) # output: b = 11:34:56

# time(hour, minute, second, microsecond)
d = time(11, 34, 56, 234566) # output: d = 11:34:56.234566
```
`time` object attributes are similar as for `datetime`:
* `b.hour`
* `b.minute`
* `b.second`
* `b.microsecond`


### Day of the week
```python
import calendar

# To get the day of the week from date as an integer. 0 = Monday, 1 = Tues, etc.
print(my_date.weekday())

# To get the name of the day of the week 
print(calendar.day_name[my_date.weekday()])
```
### ISO calendar
* Each week starts on Monday.
* The week starts counting from 1, so 1 = Monday.
```python
year, week, day = todays_date.isocalendar()
```
OR
```python
iso_date = todays_date.isocalendar() 
# returns object with 3 parameters: ISO year, ISO week number, and ISO weekday
```
### Unix Timestamp

* `datetime.timestamp(<time>)` converts a datetime object to a Unix time stamp
* `datetime.fromtimestamp(<timestamp>)` does the reverse

### `timedelta` Objects

These can be used with timedate objects to do math using operators (+ and -)
```python
#import datetime
from datetime import timedelta
# create timedelta object with difference of 2 weeks
d = timedelta(weeks=2)
```
* `timedelta.days`
* `timedelta.total_seconds()`

### Formatting Dates: More on strftime() and strptime()
```python
# current date and time
now = datetime.now()

# get year from date
year = now.strftime("%Y")
print("Year:", year)

# get month from date
month = now.strftime("%m")
print("Month;", month)

# get day from date
day = now.strftime("%d")
print("Day:", day)

# format time in HH:MM:SS
time = now.strftime("%H:%M:%S")
print("Time:", time)

# format date
date_time = now.strftime("%m/%d/%Y, %H:%M:%S")
print("Date and Time:",date_time)
```

### Handling Timezones
Create a datetime object with the timezone entered as an argument:
```Python
from pytz import timezone
londontimezone = timezone('Europe/London')
londondatetime = datetime.now(londontimezone)
print(londondatetime)
```
*See documentation for how to use these:*
* `timezone()` to specify time zone using a string argument
* `localize` to add a time zone location to a Python datetime object
* `astimezone()` to convert the existing local time zone into any other time zone we specify 

[Reference from independent search: Python pytz - GeeksforGeeks](https://www.geeksforgeeks.org/python-pytz/)
```python
# To get a list of commonly used time zones to use with the timezone function:
import pytz
  
print('Commonly used time-zones:', pytz.common_timezones, '\n')
```

### pandas Datetime Objects
```python
# import pandas module as pd
import pandas as pd
```
* Create date object using `to_datetime()` function: `pd.to_datetime("8th of sep, 2019")`
* `to_timedelta()`: Finds differences in times in terms of days, hours, minutes, and seconds.

### How to get number of days in month
[Reference: How to get number of days in month in Python (TechOverflow)](https://techoverflow.net/2019/05/16/how-to-get-number-of-days-in-month-in-python/)

```Python
from calendar import monthrange
num_days = monthrange(2019, 2)
print(num_days) # Prints a tuple of weekday of first day of month (Mon = 0), days in the month
```
[Table of Contents](#table-of-contents)

# APIs
```commandline
curl --request GET \
     --url "https://api.foursquare.com/v3/places/search?ll=45.6387,-122.6615&radius=100" \
     --header 'Accept: application/json' \
     --header 'Authorization: '"$FOURSQUARE_API_KEY"''
```

## Python API calls
[Reference: Python’s Requests Library (Guide) – Real Python](https://realpython.com/python-requests/)
### GET
```Python
import requests
import os

response = requests.get('https://api.github.com')
```
* `response.status_code` returns status code
    * If you use a `response` instance in a conditional expression, it will evaluate to `True` if the status code was between 200 and 400, and `False` otherwise
* `response.raise_for_status()` raises an `HTTPError` for certain status codes. If the response was successful, no Exception will be raised.
* `response.json()` turns JSON content into a dictionary
* `response.headers` returns the headers of the response when used alone
* `response.headers[<header key>]` allows for access to header values (case *in*sensitive)

### POST Method 
```Python
response = requests.post(<URL>, data=<dictionary or list of tuples>)

# Or, for JSON data:
response = requests.post(<URL>, json={'key':'value'})
```
### Inspecting Your Request
* `response.request.headers`
* `response.request.headers[<header key>]`
* `response.request.url`
* `response.request.body`

### Parameters in requests (follow by `=`)
* `timeout`: 
    * An integer or float representing the number of seconds to wait on a response before timing out, or
    * A tuple of 2, where:
        * first element being a connect timeout (the time it allows for the client to establish a connection to the server)
        * second being a read timeout (the time it will wait on a response once your client has established a connection)

### [Session Object](https://realpython.com/python-requests/#the-session-object)
Sessions are used to persist parameters across requests. For example, if you want to use the same authentication across multiple requests, you could use a session:
```Python
import requests
from getpass import getpass
```

### [Retry the Same Request](https://realpython.com/python-requests/#max-retries)