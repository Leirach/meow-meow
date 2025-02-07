<script setup lang="ts">
import { ref } from "vue";

const x = ref(0);
const y = ref(0);
let count = ref(0);
let buttonText = ref("No");

let angryText = "No >:(";
let veryAngryText = "Stop >:(((";

const windowWidth = (window.innerWidth - 150) / 2;
const windowHeight = (window.innerHeight - 250) / 2 ;

const moveButton = () => {
    console.log(window.innerWidth, window.innerHeight);
    console.log("range x: ", -windowWidth, 2*windowWidth);
    console.log("range y: ", -windowHeight, 2*windowHeight);

    x.value = Math.random() * 2 * windowWidth - windowWidth - 100;
    y.value = Math.random() * 2 * windowHeight - windowHeight -100;

    console.log(x.value, y.value);

    count.value++;
    if (count.value >= 5) buttonText.value = angryText;
    if (count.value >= 10) buttonText.value = veryAngryText;
};

</script>

<template>
    <button @mouseover="moveButton" @click="moveButton" class="moving-button"
        :style="{ transform: `translate(${x}px, ${y}px)` }">
        {{ buttonText }}
    </button>
</template>

<style scoped>
.moving-button {
    position: relative;
    transition: transform 0.2s ease-in-out;
    padding: 10px 20px;
    font-size: 16px;
    cursor: pointer;
    border: none;
    background-color: #9D152D;
    color: white;
    border-radius: 5px;
    filter: drop-shadow(0 0 1em #9D152D);
}
</style>
