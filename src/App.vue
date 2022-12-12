<template>
  <canvas id="canvas"></canvas>
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
import { onMounted } from 'vue';

onMounted(() => {
  let camera = new Instacam(document.querySelector('#canvas'), {
    mode: 'back',
    invert: 1,
  });
  camera.invert = 1;
});
</script>
