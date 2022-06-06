// geolocalizacion de la persona

const API_KEY = 'dd412f6a3ff6ee28c2d0b846ceba2c46';

const log = position => {
    const{ latitude, longitude} = position.coords;
    fetch(`https://api.openweathermap.org/data/2.5/weather?units=metric&lat=${latitude}&lon=${longitude}&appid=${API_KEY}`)
    .then(response => response.json())
    .then(data => setWeatherData(data))
    
   
}

const setWeatherData = data => {
    console.log(data);
    // aca dentro vamos a poner toda la info que se recibe del html
    const weatherData = {
        location: data.name,
        description: data.weather[0].main,
        humidity: data.main.humidity,
        pressure: data.main.pressure,
        temperature: data.main.temp,
        date: getDate(),
    }

    Object.keys(weatherData).forEach( key => {
        document.getElementById(key).textContent = weatherData[key];
    });

    cleanUp();

    }

    const cleanUp = () => {
        let container = document.getElementById('container');
        let loader = document.getElementById('loader');

        loader.style.display = 'none';
        container.style.display = 'flex';
    }

    const getDate = () => {
        let date = new Date();
        return `${date.getDate()}-${ ('0' + (date.getMonth() + 1)).slice(-2)}-${date.getFullYear()}`;


}
const onLoad = () => {
    navigator.geolocation.getCurrentPosition(log);
}