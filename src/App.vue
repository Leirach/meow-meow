<script setup lang="ts">
import MovingButton from './components/MovingButton.vue'
import { ref, onMounted } from "vue";

const yippieVisible = ref(false);
const audio = new Audio('/yippie.mp3'); // Set your MP3 file path

const showYippie = () => {
  if (yippieVisible.value) return;

  yippieVisible.value = true;
  audio.play();
};

onMounted(() => {
  audio.load();
  audio.volume = 0.5;
  audio.addEventListener('ended', () => {
    yippieVisible.value = false;
  });
});
</script>

<template>
  <div class="container">
    <img src="/meow.jpg" class="main-image" />
    <h1>Will you be my meow meow?</h1>

    <div class="buttons-container">
      <button class="yes-button" @click="showYippie">Yes</button>
      <div class="spacer"></div>
      <MovingButton></MovingButton>
    </div>
    <div>
      <img src="/meow2.jpg" class="main-image" />
    </div>

    <img v-if="yippieVisible" src="/yippie.gif" class="yippie" />
  </div>
</template>

<style scoped>
h1 {
  color: #C88AC3;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 0;
  height: 90vh;
}

button {
  width: 150px;
}

.buttons-container {
  display: flex;
  gap: 20px;
  margin-bottom: 20px;
}

.spacer {
  flex: 1
}

.yes-button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  border: none;
  background-color: #C88AC3;
  color: white;
  border-radius: 5px;
  filter: drop-shadow(0 0 1em #C88AC3);
}

.main-image {
  width: 30vh;
  height: auto;
  margin-bottom: 20px;
}

.yippie {
  position: absolute;
  width: 100vw;
  height: auto;
}
</style>
