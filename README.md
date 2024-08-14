# quickWeather
# python3
# quickWeather.py - Prints the weather for a location from the command line

import json, sys, requests

# Computer location from command line arguments
if len(sys.argv) < 2:
    print("Usage:quickWeather.py location")
    sys.exit()

location = ' '.join(sys.argv[1:])

url = "http://api.openweathermap.org/data/2.5/weather?q=%s&app_id=20853a741eb730eaa677d5fc79f9838e" % location
response = requests.get(url)
response.raise_for_status()

weatherData = json.loads(response.text)

data = weatherData['weather']
print('Current weather in %s:' % (location))
print(data[0]['main'], "-", data[0]['description'])

temp = weatherData['main']
print("Temperature is:', temp['temp']-273.15,""C")
print()
