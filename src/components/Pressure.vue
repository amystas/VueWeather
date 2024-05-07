<script setup>
    import { defineProps } from 'vue';
    const props = defineProps(['pressure'])
</script>

<template>
    <div>
        <p id="label"><i class="ri-speed-up-line"></i> Ciśnienie</p>
        <p id="value">{{ props.pressure }} <span>hPa</span></p>
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
        margin: 10px 3px 0px 3px;
    }
    #label {
        color: rgb(157, 208, 255);
        margin-top: 0;
    }
    #value {
        font-size: 2rem;
    }
    span {
        font-size: 1.2rem;
    }
</style>