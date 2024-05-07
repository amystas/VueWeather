<script setup>
import { ref, computed, defineProps, watch } from 'vue';
const props = defineProps(['appid', 'lat', 'lon', 'units', 'unit']);
var url = computed(() => 'https://api.openweathermap.org/data/2.5/forecast?lat=' + props.lat + '&lon=' + props.lon + '&cnt=10&appid=' + props.appid + '&units=' + props.units);
var data = ref({});
var forecastList = ref({});

async function load() {
    fetch(url.value)
        .then(response => response.json())
        .then(result => data.value = result)
        .then(() => {
            forecastList.value = data.value.list;
        });
}

const getIcon = (icon) => `src/icons/${icon}.png`;

watch(
    () => props,
    async () => {
        await load();
    },
    { immediate: true, deep: true },
);
</script>

<template>
    <div id="hourlyForecast">
        <div v-for="forecast in forecastList">
            <p>{{ new Date(forecast.dt_txt).getHours() }}:00</p>
            <img :src="getIcon(forecast.weather[0].icon)" alt="">
            <p>{{ Math.round(forecast.main.temp) }} {{ props.unit }}</p>
        </div>
    </div>
</template>

<style scoped>
#hourlyForecast {
    display: flex;
    align-items: flex-end;
    font-family: "Helvetica Neue";
    color: white;
    background-color: rgba(51, 108, 175, 0.627);
    width: 600px;
    border-radius: 12px;
    margin-left: 10px;
    padding: 20px 10px;
}

#hourlyForecast div {
    flex-basis: 60px;
}

p {
    text-align: center;
}

img {
    height: 50px;
    width: 50px;
}
</style>