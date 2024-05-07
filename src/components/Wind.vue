<script setup>
  import { defineProps, ref } from 'vue';
  const props = defineProps(['angle', 'windspeed', 'unit']);
</script>
<template>
    <div id="wind">
        <p id="label"><i class="ri-windy-line"></i> Wiatr</p>
    <div style="display: flex; align-items: center;">
    <div class="compass">
      <!-- Arrow -->
      <svg class="compass__arrow" :style="`transform: rotate(${props.angle}deg);`" width="100" height="100" viewBox="0 0 37 36" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
          <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
              <g id="spot-search-copy-10" transform="translate(-236.000000, -796.000000)">
                  <g id="Group" transform="translate(236.000000, 796.000000)">
                      <rect id="Rectangle" opacity="0" x="0.5" y="0" width="100" height="100"></rect>
                      <polygon id="Rectangle" fill="#FFFFFF" points="14 18 18.5 7 23 18 18.5292306 29"></polygon>
                      <polygon id="Rectangle" fill="#5BC0EB" transform="translate(18.500000, 12.500000) scale(1, -1) translate(-18.500000, -12.500000) " points="14 7 23 7 18.5292306 18"></polygon>
                      <circle id="Oval" fill="#000000" cx="18.5" cy="18" r="1.5"></circle>
                  </g>
              </g>
          </g>
      </svg>
      <!-- BG dots -->
      <svg class="compass__background" width="37px" height="36px" viewBox="0 0 37 36" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
          <g id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
              <g id="spot-search-copy-10" transform="translate(-236.000000, -796.000000)">
                  <rect id="bg" opacity="0" x="236.5" y="796" width="36" height="36"></rect>
                  <circle id="nn" fill="#FFFFFF" cx="254.5" cy="797.5" r="1.5"></circle>
                  <circle id="ss" fill="#FFFFFF" cx="254.5" cy="830.5" r="1.5"></circle>
                  <circle id="ee" fill="#FFFFFF" cx="271"   cy="814"   r="1.5"></circle>
                  <circle id="ww" fill="#FFFFFF" cx="238"   cy="814"   r="1.5"></circle>
                  <circle id="nw" fill="#FFFFFF" cx="242.5" cy="802.5" r="1"  ></circle>
                  <circle id="sw" fill="#FFFFFF" cx="242.5" cy="825.5" r="1"  ></circle>
                  <circle id="ew" fill="#FFFFFF" cx="266.5" cy="825.5" r="1"  ></circle>
                  <circle id="ne" fill="#FFFFFF" cx="266.5" cy="802.5" r="1"  ></circle>
              </g>
          </g>
      </svg>
    </div>
    <p><span>{{ props.windspeed }}</span> {{ props.unit }}</p>
    </div>
    </div>
  </template>
  
  <style scoped>
  .compass {
    position: relative;
    height: 50px;
    width: 50px;
  }
  .compass__arrow, .compass__background {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  #wind {
        color: white;
        background-color: rgba(51, 108, 175, 0.627);
        border-radius: 12px;
        padding: 5px 20px 10px 5px;
        width: 140px;
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
      font-size: 2rem;
    } p {
      margin-left: 10px;
    }
  </style>