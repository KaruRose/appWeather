<template>
  <div class="flex gap-10">
    <div class="card card-compact w-96 bg-base-100 shadow-xl">
      <div class="card-body flex justify-center items-center">
        <h1 class="card-title text-6xl text-cyan-600">{{ temp }} °C</h1>
      </div>
    </div>

    <div class="card card-compact w-96 bg-base-100 shadow-xl">
      <div class="card-body flex justify-start">
      <figure>
        <img
          id="weather-icon"
          v-if="weatherIcon.src != ''"
          :src="weatherIcon.src"
          alt=""
          width="150"
          height="150"
        />
      </figure>
        <h2 class="card-title text-6xl justify-center text-cyan-600">{{ city }}</h2>
      </div>
    </div>

    <div class="card card-compact w-96 h-96 bg-base-100 shadow-xl">
      <div class="card-body flex justify-center items-center">
        <h1 class="card-title justify-center text-6xl text-cyan-600">{{ status }}</h1>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const temp = ref("");

const status = ref("");

const city = ref("");

const weatherIcon = ref({
  src: "",
});

window.addEventListener("load", () => {
  let temperatura = document.getElementById;
  let descripcion = document.getElementById;

  let ubicacion = document.getElementById;
  let imagen = document.getElementById;

  let vientoVelocidad = document.getElementById;

  let lat;
  let lon;

  if (navigator.geolocation) {
    navigator.geolocation.getCurrentPosition((posicion) => {
      lon = posicion.coords.longitude;
      lat = posicion.coords.latitude;
      // Ubicacion Actual
      // const ulr = `https://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&appid=cd60bc056ea10f247a68dda3ee815665`;

      // Ubicacion por ciudad
      const url = `https://api.openweathermap.org/data/2.5/weather?q=Merida&lang=es&units=metric&appid=cd60bc056ea10f247a68dda3ee815665`;

      fetch(url)
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          console.log(data);
          temp.value = data.main.temp;
          city.value = data.name;
          status.value = data.weather[0].description;
          console.log(temp.value)

          let caseData = data.weather[0].main;
          console.log(caseData)
          if (caseData === "Clear") {
            weatherIcon.value.src = "/appWeather/animated_icons/day.svg";
            console.log(weatherIcon.value.src);
          }

          if (caseData === "Clouds") {
            weatherIcon.value.src = "/appWeather/animated_icons/cloudy-day-2.svg";
            console.log(weatherIcon.value.src);
          }

          if (caseData === "Rain") {
            weatherIcon.value.src = "/appWeather/animated_icons/rainy-2.svg";
            console.log(weatherIcon.value.src);
          }

          if (caseData === "Thunderstorm") {
            weatherIcon.value.src = "/appWeather/animated_icons/thunder.svg";
            console.log(weatherIcon.value.src);
          }
        })

        .catch((error) => {
          console.log(error);
        });
    });
  }
});
</script>