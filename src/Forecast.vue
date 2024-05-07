<script setup>
import BriefInfo from './components/BriefInfo.vue';
import HourlyForecast from './components/HourlyForecast.vue';
import Humidity from './components/Humidity.vue';
import Pressure from './components/Pressure.vue';
import FeelsLike from './components/FeelsLike.vue';
import Wind from './components/Wind.vue';
import { computed, ref, defineProps, watch } from 'vue';

const props = defineProps(['appid', 'lon', 'lat', 'lang', 'units']);

var unit = ref('°C');
var speedUnit = ref('km/h');
var speedMultiplier = ref(3.6);


//var url = computed(() => 'https://api.openweathermap.org/data/2.5/weather?q=' + props.city + '&appid=' + props.appid + '&units=' + props.units + '&lang=' + props.lang);
var url = computed(() => 'https://api.openweathermap.org/data/2.5/weather?lat=' + props.lat + '&lon=' + props.lon + '&appid=' + props.appid + '&units=' + props.units + '&lang=' + props.lang);
var data = ref();

var rainy = ["słabe opady deszczu", "umiarkowane opady deszczu"];
var cloudy = ["pochmurnie", "zachmurzenie duże", "zachmurzenie umiarkowane", "zachmurzenie małe"];
var clear = ["bezchmurnie"];

// const response = await fetch(url.value);
//     const result = await response.json();
//     data.value = result;

async function load() {
fetch(url.value)
    .then(response => response.json())
    .then(result => data.value = result)
    .then(() => {
        document.body.style.backgroundRepeat = 'no-repeat';
        document.body.style.backgroundSize = 'cover';
        if (cloudy.includes(data.value.weather[0].description)) {
            document.body.style.backgroundImage = 'url(src/backgrounds/cloudy.jpg)';
        } else if(rainy.includes(data.value.weather[0].description)) {
            document.body.style.backgroundImage = 'url(src/backgrounds/rain.jpg)';
        } else if(clear.includes(data.value.weather[0].description)) {
            document.body.style.backgroundImage = 'url(src/backgrounds/clear.jpg)';
        }
    });
}

watch(
    () => props,
    async () => {

        await load();
        if (props.units == 'imperial') {
            unit.value = '°F';
            speedUnit.value = 'mph';
            speedMultiplier.value = 1;
        } else if (props.units == 'metric') {
            unit.value = '°C';
            speedUnit.value = 'km/h';
            speedMultiplier.value = 3.6;
        }
    },
    { immediate: true, deep: true },
);
</script>

<template>
    <div style="display: flex;"  v-if="data">
        <BriefInfo :cityName="data.name" :temp="Math.round(data.main.temp)" :desc="data.weather[0].description"
            :minTemp="Math.round(data.main.temp_min)" :maxTemp="Math.round(data.main.temp_max)" :unit="unit">
        </BriefInfo>
        <div>
            <HourlyForecast :unit="unit" :units="props.units" :appid="props.appid" :lat="props.lat" :lon="props.lon"></HourlyForecast>
            <div style="display: flex;">
                <Humidity :humidity="data.main.humidity"></Humidity>
                <Pressure :pressure="data.main.pressure"></Pressure>
                <FeelsLike :feelsLike="Math.round(data.main.feels_like)" :unit="unit"></FeelsLike>
                <Wind :unit="speedUnit" :angle="data.wind.deg" :windspeed="Math.round(Number(data.wind.speed)*speedMultiplier)"></Wind>
            </div>
        </div>
    </div>
</template>