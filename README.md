npx create-react-app weather-app
cd weather-app
npm install axios
import React, { useState, useEffect } from 'react';
import axios from 'axios';

const Weather = () => {
  const [weatherData, setWeatherData] = useState(null);
  const API_KEY = 'YOUR_API_KEY';
  const CITY_NAME = 'London'; // Replace with the desired city name

  useEffect(() => {
    const fetchWeatherData = async () => {
      try {
        const response = await axios.get(
          https://api.openweathermap.org/data/2.5/weather?q=${CITY_NAME}&appid=${API_KEY}
        );
        setWeatherData(response.data);
      } catch (error) {
        console.error('Error fetching weather data:', error);
      }
    };

    fetchWeatherData();
  }, []);

  if (!weatherData) {
    return <div>Loading...</div>;
  }

  const { main, description } = weatherData.weather[0];
  const { temp, humidity } = weatherData.main;
  const windSpeed = weatherData.wind.speed;

  return (
    <div>
      <h2>Weather Forecast for {CITY_NAME}</h2>
      <p>
        <strong>Temperature:</strong> {Math.round(temp - 273.15)}°C
      </p>
      <p>
        <strong>Humidity:</strong> {humidity}%
      </p>
      <p>
        <strong>Wind Speed:</strong> {windSpeed} m/s
      </p>
      <p>
        <strong>Description:</strong> {description}
      </p>
    </div>
  );
};

export default Weather;
import React from 'react';
import Weather from './Weather';

const App = () => {
  return (
    <div className="App">
      <Weather />
    </div>
  );
};

export default App;
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
npm start
