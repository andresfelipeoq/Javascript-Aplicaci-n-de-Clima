# Javascript-Aplicaci-n-de-Clima
Aplicación de Clima
Crear una aplicación de clima en JavaScript es un proyecto que involucra la obtención de datos de pronóstico meteorológico de una fuente externa, como una API de clima, y luego mostrar esos datos en una interfaz de usuario. Aquí tienes un ejemplo corto de cómo puedes comenzar a construir una aplicación de clima en JavaScript utilizando la API de OpenWeatherMap:

1. Regístrate en OpenWeatherMap:
   - Ve al sitio web de OpenWeatherMap (https://openweathermap.org/) y regístrate para obtener una clave de API gratuita. Esta clave es necesaria para acceder a los datos de pronóstico.

2. Configura tu proyecto:
   - Crea una carpeta para tu proyecto e inicia un nuevo archivo HTML y otro archivo JavaScript. Por ejemplo, puedes nombrarlos "index.html" y "app.js".

3. Estructura básica del archivo HTML (index.html):

```html
<!DOCTYPE html>
<html>
<head>
    <title>Aplicación de Clima</title>
</head>
<body>
    <h1>Aplicación de Clima</h1>
    <input type="text" id="cityInput" placeholder="Ingresa una ciudad">
    <button id="searchBtn">Buscar</button>
    <div id="weatherInfo"></div>

    <script src="app.js"></script>
</body>
</html>
```

4. Código JavaScript básico (app.js):

```javascript
// Replace 'TU_CLAVE_DE_API' con la clave de API que obtuviste de OpenWeatherMap.
const API_KEY = 'TU_CLAVE_DE_API';
const BASE_URL = 'https://api.openweathermap.org/data/2.5/weather';

document.getElementById('searchBtn').addEventListener('click', () => {
    const city = document.getElementById('cityInput').value;
    getWeatherData(city);
});

function getWeatherData(city) {
    const url = `${BASE_URL}?q=${city}&appid=${API_KEY}&units=metric`;
    
    fetch(url)
        .then(response => response.json())
        .then(data => {
            displayWeather(data);
        })
        .catch(error => {
            console.error('Error al obtener datos del clima', error);
        });
}

function displayWeather(data) {
    const weatherInfo = document.getElementById('weatherInfo');
    weatherInfo.innerHTML = `
        <h2>Clima en ${data.name}, ${data.sys.country}</h2>
        <p>Temperatura: ${data.main.temp}°C</p>
        <p>Clima: ${data.weather[0].description}</p>
    `;
}
```

Este ejemplo utiliza la API de OpenWeatherMap para obtener datos de clima según la ciudad ingresada por el usuario. Los datos se muestran en una página web simple. Asegúrate de incluir tu clave de API en el código y ten en cuenta que este es solo un ejemplo básico para comenzar. Puedes personalizar y ampliar esta aplicación según tus necesidades.
