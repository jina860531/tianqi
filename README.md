import json
import requests

def weather_forecast(city):
    api_key = 'YOUR_API_KEY' 
    url = f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric'

    response = requests.get(url)
    data = json.loads(response.text)
    
    forecast = {}
    forecast['city'] = data['name']
    forecast['temperature'] = data['main']['temp']
    forecast['description'] = data['weather'][0]['description']
    forecast['humidity'] = data['main']['humidity']
    forecast['wind_speed'] = data['wind']['speed']
    
    print(f"Weather forecast for {forecast['city']}") 
    print(f"Temperature: {forecast['temperature']} C")
    print(f"Conditions: {forecast['description']}")
    print(f"Humidity: {forecast['humidity']}%")
    print(f"Wind Speed: {forecast['wind_speed']} km/h")
    
city = input("Enter city name: ")
weather_forecast(city)
这个代码使用OpenWeatherMap的API获取
