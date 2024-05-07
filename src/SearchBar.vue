<script setup>
import { ref, watch } from 'vue';
const props = defineProps(['appid']);
var inputValue = ref('');
var data = ref([]);

var showSuggestions = ref(false);

function getResults(city) {
    const url = "https://api.openweathermap.org/geo/1.0/direct?appid="+props.appid+"&q="+city+"&limit=5";
    fetch(url)
    .then(response => response.json())
    .then(result => data.value = result);
}

watch(inputValue, (newValue, oldValue) => {
  if (newValue.length > 2) {
    getResults(newValue);
    showSuggestions.value = true;
  } else if(newValue.length === 0) {
    showSuggestions.value = false;
  }
});

</script>

<template>
    <div id="searchField">
        <i class="ri-search-line"></i><input type="text" name="search" id="search" v-model="inputValue" placeholder="Szukaj">
        <div v-if="showSuggestions">
            <p v-for="city in data" @click="$emit('onCityChange', city)">{{ city.name }}, {{ city.state }}, {{ city.country }}</p>
        </div>
    </div>
</template>

<style scoped>
#searchField
{
    background-color: rgba(51, 108, 175, 0.627);
    border-radius: 12px;
    padding: 10px;
    width: 15rem;
    color: rgba(255, 255, 255, 0.627);
}
#searchField input 
{
    background: transparent;
    border: none;
    color: white;
    padding-left: 10px;
}
input:focus
{
    outline: none;
}
</style>