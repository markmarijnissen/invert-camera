<template>
  <div @click.prevent="switchMode">
    <canvas id="canvas"></canvas>
  </div>
</template>
<style scoped>
canvas {
  width: 98vw;
  height: 98vh;
  object-fit: contain;
}
</style>
<script setup>
import Instacam from 'instacam';
import { onMounted, ref, watch } from 'vue';

const mode = ref('front');
let camera;

watch(mode, () => (camera.mode = mode.value));

onMounted(() => {
  camera = new Instacam(document.querySelector('#canvas'), {
    mode: mode.value,
    invert: 1,
  });
  camera.invert = 1;
});

function switchMode() {
  mode.value = mode.value === 'back' ? 'front' : 'back';
}
</script>
