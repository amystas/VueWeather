<script setup>
    import {ref, computed} from 'vue';

    const props = defineProps(['humidity']);
</script>

<template>
    <div>
        <p id="label"><i class="ri-water-percent-line"></i> Wilgotność</p>
        <p id="value">{{ props.humidity }}%</p>
    </div>
</template>

<style scoped>
    div {
        color: white;
        background-color: rgba(51, 108, 175, 0.627);
        border-radius: 12px;
        padding: 5px 20px 10px 5px;
        width: 120px;
        font-family: "Helvetica Neue";
        margin: 10px 3px 0px 10px;
    }
    #label {
        color: rgb(157, 208, 255);
        margin-top: 0;
    }
    #value {
        font-size: 2rem;
    }
</style>