# Simple charting DynISF

## prerequisties

- Python 3
- Python requests library. You can install with ```pip install requests``` for best in a virtual environment and not the system environment.
- already active usage of DynISF with available data for the last 6 hours in your Nightscout database.

## python code

As image with short explanaition of what to change.

![](./images/Bildschirmfoto%20vom%202024-02-11%2013-38-27.png)


As code for copy and paste.

``` python
import requests
import statistics
from datetime import datetime, timezone, timedelta

start = datetime.now()
#myTimeSlot = timedelta(days=1)
myTimeSlot = timedelta(hours=6)
start -= myTimeSlot
startMillis = int(start.timestamp()*1000)

# get the JWT token from the Nightscout server for further calls by providing the access token
api_url = "https://NightscoutURL/api/v2/authorization/request/yourAcessToken"
response = requests.get(api_url)

# the JWT token is provided in the token field of the response
# print (response.json()["token"])
# print (response.json())
# put the JWT token as Bearer token in the request header
myheaders = { 'Authorization' : 'Bearer ' + response.json()["token"] }
# print(myheaders)

# get data since start
api_url = "https://NightscoutURL/api/v3/devicestatus?limit=1000&fields=created_at,openaps&sort$desc=created_at&date$gte=" + str(startMillis)

response = requests.get(url = api_url, headers = myheaders)

# print the headline of the table
print("Datetime, VariableSense")

for x in response.json()["result"]:
    # check that variable_sens is that for entry in result
    if "openaps" in x and "suggested" in x["openaps"] and "variable_sens" in x["openaps"]["suggested"]:
        print(x["created_at"],
            ",",
            x["openaps"]["suggested"]["variable_sens"])
```

## run the Python code and look at the result

![](./images/Bildschirmfoto%20vom%202024-02-11%2013-47-16.png)

## run the Python code and pipe output into file

![](./images/Bildschirmfoto%20vom%202024-02-11%2014-06-23.png)

## import csv-file into your favorite spreadsheet application

I use Google Sheets but it's basic functionality though you should be able to use Excel or others too but I have not tested.

Mark the imported data and via "Insert->Chart" create a chart from it.
You can resize it with the mouse easily.

![](./images/Bildschirmfoto%20vom%202024-02-11%2013-49-58.png)


## adapting the timeframe

You can easily change the timeframe in the code.
Look at the line below and change the hours or even days.

Run it again, pipe it into file and import it.

``` python
myTimeSlot = timedelta(hours=6)
```
