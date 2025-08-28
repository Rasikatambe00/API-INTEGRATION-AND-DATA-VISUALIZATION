import requests
import matplotlib.pyplot as plt

# Replace with your OpenWeatherMap API key
API_KEY = "c90c454d60c9e613c7f0636ee84b5943"
CITY = "Mumbai"
URL = f"http://api.openweathermap.org/data/2.5/forecast?q={CITY}&appid={API_KEY}&units=metric"

response = requests.get(URL)
data = response.json()

# Extract temperatures & dates
dates = [item['dt_txt'] for item in data['list'][:10]]
temps = [item['main']['temp'] for item in data['list'][:10]]

# Plot
plt.plot(dates, temps, marker='o')
plt.xticks(rotation=45)
plt.title(f"Temperature Forecast for {CITY}")
plt.xlabel("Date & Time")
plt.ylabel("Temperature (°C)")
plt.show()
