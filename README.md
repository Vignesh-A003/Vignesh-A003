import requests

def get_weather(city):
    api_key = 'YOUR_API_KEY'  # Replace 'YOUR_API_KEY' with your OpenWeatherMap API key
    url = f'http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric'
    response = requests.get(url)
    data = response.json()
    if data['cod'] == 200:
        weather_desc = data['weather'][0]['description']
        temp = data['main']['temp']
        humidity = data['main']['humidity']
        wind_speed = data['wind']['speed']
        print(f'Weather in {city}:')
        print(f'Description: {weather_desc}')
        print(f'Temperature: {temp}°C')
        print(f'Humidity: {humidity}%')
        print(f'Wind Speed: {wind_speed} m/s')
    else:
        print('City not found. Please try again.')

def main():
    city = input('Enter the city name: ')
    get_weather(city)

if __name__ == "__main__":
    main()
