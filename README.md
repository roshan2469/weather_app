📄 Project Title
Weather App using HTML, CSS, and JavaScript with OpenWeather API

1. Objective
The objective of this project is to develop a web-based weather application that allows users to search for any city and view real-time weather details such as temperature, weather conditions, humidity, and wind speed using an external API.

2. Description
The Weather App is a simple, interactive, and responsive web application that fetches weather data from the OpenWeatherMap API and displays it in a user-friendly interface.
It demonstrates the integration of front-end web development with REST APIs to provide live data to users.

3. Features
Search weather by city name

Displays temperature, condition, humidity, and wind speed

Shows weather icons for better visual representation

Real-time API integration with OpenWeatherMap

Mobile-friendly responsive design

4. Technology Stack
Language: HTML, CSS, JavaScript

API Used: OpenWeatherMap API

Platform: Browser-based

Libraries Used: None (pure JavaScript fetch)

5. How It Works
HTML creates the layout for search input and weather display.

CSS styles the app for an attractive look.

JavaScript handles:

Capturing user input (city name)

Sending API requests using fetch()

Parsing JSON response

Dynamically updating HTML elements with weather data

6. Applications
Weather checking tool for websites

Educational project for API usage

Travel and location-based services integration

7. Limitations
Requires internet connection to fetch API data

Limited to API rate limits of OpenWeatherMap

Accuracy depends on API data source

8. How to Use the Code
Step 1: Get an OpenWeatherMap API Key
Go to https://openweathermap.org/api

Sign up and log in.

Generate a free API key (usually takes a few minutes to activate).

Step 2: Save the Code in Three Files
index.html
html
Copy
Edit
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Weather App</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="weather-container">
        <h1>Weather App</h1>
        <input type="text" id="cityInput" placeholder="Enter city name">
        <button onclick="getWeather()">Get Weather</button>
        <div id="weatherResult"></div>
    </div>
    <script src="script.js"></script>
</body>
</html>
style.css
css
Copy
Edit
body {
    font-family: Arial, sans-serif;
    background: linear-gradient(to right, #00c6ff, #0072ff);
    text-align: center;
    color: white;
}

.weather-container {
    margin-top: 100px;
}

input {
    padding: 10px;
    border: none;
    border-radius: 5px;
}

button {
    padding: 10px 15px;
    margin-left: 5px;
    border: none;
    background: #ff9800;
    color: white;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background: #e68900;
}

#weatherResult {
    margin-top: 20px;
    font-size: 18px;
}
script.js
javascript
Copy
Edit
const apiKey = "YOUR_API_KEY"; // Replace with your OpenWeatherMap API key

function getWeather() {
    const city = document.getElementById("cityInput").value;
    if (city === "") {
        alert("Please enter a city name");
        return;
    }

    fetch(`https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`)
        .then(response => response.json())
        .then(data => {
            if (data.cod === "404") {
                document.getElementById("weatherResult").innerHTML = "City not found!";
                return;
            }
            document.getElementById("weatherResult").innerHTML = `
                <h2>${data.name}, ${data.sys.country}</h2>
                <p>Temperature: ${data.main.temp}°C</p>
                <p>Condition: ${data.weather[0].description}</p>
                <p>Humidity: ${data.main.humidity}%</p>
                <p>Wind Speed: ${data.wind.speed} m/s</p>
            `;
        })
        .catch(error => {
            document.getElementById("weatherResult").innerHTML = "Error fetching data";
        });
}
Step 3: Run the App
Save all three files (index.html, style.css, script.js) in the same folder.

Replace "YOUR_API_KEY" in script.js with your actual OpenWeatherMap API key.

Open index.html in your browser.

Type a city name and click "Get Weather".
# weather_app
