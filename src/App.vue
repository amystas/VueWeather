<script setup>
  import {ref, reactive} from 'vue';
  import Forecast from './Forecast.vue';
  import SearchBar from './SearchBar.vue';
  import UnitChange from './UnitChange.vue';

  var key = ref('36bb972eb44abc7137a2a84bd63afd71');
  var lat = ref('53.4301818');
  var lon = ref('14.5509623');
  var lang = ref('pl');
  var units = ref('metric');
  
  function changeCity(city) {
    console.log(city.lat, city.lon);
    lat.value = city.lat;
    lon.value = city.lon;
  }

  function unitToImperial() {
    units.value = 'imperial';
  }

  function unitToMetric() {
    units.value = 'metric';
  }
</script>

<template>
  <UnitChange @toImperial="unitToImperial" @toMetric="unitToMetric"
  style="position: absolute; right: 280px; top: 10px"></UnitChange>
  <SearchBar :appid="key" @onCityChange="changeCity" 
  style="position: absolute; right: 10px; top: 10px"></SearchBar>
  <Forecast :appid="key" :lat="lat" :lon="lon" :lang="lang" :units="units" id="forecast"></Forecast>
</template>

<style scoped>
#forecast {
    width: 70vw;
    margin-top: 25vh;
    margin-left: 15vw;
}
</style>