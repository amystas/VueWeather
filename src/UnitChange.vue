<script setup>
    defineEmits(['toImperial', 'toMetric']);
</script>

<template>
    <section>
        <div @click="$emit('toMetric')" id="metric">&deg;C</div>
        <div @click="$emit('toImperial')" id="imperial">&deg;F</div>
    </section>
</template>

<style scoped>
    section {
        display: flex;
    }
    div {
        font-family: 'Helvetica Neue';
        background-color: rgba(51, 108, 175, 0.627);
        padding: 10px;
        border-radius: 10px;
    }
    #metric {
        border-bottom-right-radius: 0;
        border-top-right-radius: 0;
    }
    #imperial {
        border-bottom-left-radius: 0;
        border-top-left-radius: 0;
    }
    div:active {
        background-color: rgba(84, 122, 165, 0.627);
    }
</style>