<script setup>
    const emit = defineEmits(['toImperial', 'toMetric']);
    function metricSelected() {
        document.getElementById('metric').style.backgroundColor="rgba(80, 142, 213, 0.627)";
        document.getElementById('imperial').style.backgroundColor="rgba(51, 108, 175, 0.627)";
        emit("toMetric");
    }
    function imperialSelected() {
        document.getElementById('imperial').style.backgroundColor="rgba(80, 142, 213, 0.627)";
        document.getElementById('metric').style.backgroundColor="rgba(51, 108, 175, 0.627)";
        emit("toImperial");
    }
</script>

<template>
    <section>
        <div @click="metricSelected" id="metric">&deg;C</div>
        <div @click="imperialSelected" id="imperial">&deg;F</div>
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
        background-color: rgba(80, 142, 213, 0.627);
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