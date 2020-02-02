# "API Client" Exercise (Python)

## Prerequisites

  + [The "Web Scraper" Exercise](/exercises/web-scraper/exercise.md)

## Instructions

In your "web-scraper-exercise" directory, create a new file called "api_client.py" and insert the following contents:

```py
# web-scraper-exercise/api_client.py

import requests
import json

print("-----------------------")
print("API CLIENT EXERCISE...")
print("-----------------------")

symbol = "MSFT"
request_url = "https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&apikey=abc123&symbol=" + symbol
print("REQUEST URL:", request_url)

# issue an HTTP "GET" request to the specified URL:
response = requests.get(request_url)
print("RESPONSE:", response)
print(response.status_code)
print(response.text) # the response data!

print("-----------------------")
print("PARSING THE RESPONSE:")
print("-----------------------")

# use the json module to parse the JSON-formatted response data and convert it to a dictionary object
# see: https://docs.python.org/3/library/json.html
parsed_response = json.loads(response.text)
print(parsed_response)

# access nested attributes of the dictionary object
# see: https://docs.python.org/3/library/stdtypes.html#dict
time_series = parsed_response["Time Series (Daily)"]

# loop through all daily price objects:
# see: https://docs.python.org/3/tutorial/datastructures.html#looping-techniques
for date, prices in time_series.items():
    print("DATE:", date)
    print(prices)
    print("---")
```

Run the script from the command-line and observe the printed output:

```sh
python api_client.py
```

Alright, we've demonstrated our ability to parse the API response. Now let's do something with the data, like store each day's closing price in a CSV file:

```py
# web-scraper-exercise/api_client.py

import requests
import json
import csv

print("-----------------------")
print("API CLIENT EXERCISE...")
print("-----------------------")

symbol = "MSFT"
request_url = "https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&apikey=abc123&symbol=" + symbol
print("REQUEST URL:", request_url)

# issue an HTTP "GET" request to the specified URL:
response = requests.get(request_url)
print("RESPONSE:", response)
print(response.status_code)
print(response.text) # the response data!

print("-----------------------")
print("PARSING THE RESPONSE:")
print("-----------------------")

# use the json module to parse the JSON-formatted response data and convert it to a dictionary object
# see: https://docs.python.org/3/library/json.html
parsed_response = json.loads(response.text)
print(parsed_response)

# access nested attributes of the dictionary object
# see: https://docs.python.org/3/library/stdtypes.html#dict
time_series = parsed_response["Time Series (Daily)"]

# loop through all daily price objects:
# see: https://docs.python.org/3/tutorial/datastructures.html#looping-techniques
for date, prices in time_series.items():
    print("DATE:", date)
    print(prices)
    print("---")

print("-----------------------")
print("WRITING TO CSV...")
print("-----------------------")

with open(f"prices_{symbol}.csv", "w") as csv_file:
    # see: https://docs.python.org/3/library/csv.html#csv.DictWriter
    writer = csv.DictWriter(csv_file, fieldnames=["symbol", "date", "closing_price"])
    # writes header row with fieldnames set above:
    writer.writeheader()

    # loop through all daily price objects and write each to its own row:
    for date, prices in time_series.items():
        writer.writerow({
            "symbol": symbol,
            "date": date,
            "closing_price": prices["4. close"]
        })

```

Run the script again from the command-line and observe the printed output:

```sh
python api_client.py
```
