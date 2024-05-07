<script setup>
    import {ref, computed} from 'vue';
    const props = defineProps(['cityName', 'temp', 'desc', 'minTemp', 'maxTemp', 'unit']);
</script>

<template>
<div>
    <h3>{{ props.cityName }}</h3>
    <h1>{{ props.temp }}{{props.unit}}</h1>
    <p>{{ props.desc }}</p>
    <p>Od {{ props.minTemp }}{{props.unit}} do {{ props.maxTemp }}{{ props.unit }}</p>
</div>
</template>

<style scoped>
div {
    font-family: "Helvetica Neue";
    width: 200px;
    color: white;
    background-color: rgba(51, 108, 175, 0.627);
    padding: 20px 60px;
    font-size: 1.4rem;
    border-radius: 12px;
}
div *{
    text-align: center;
}
</style>