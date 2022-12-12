<template>
  <div>
    <select v-model="mode">
      <option value="front">Front</option>
      <option value="back">Back</option>
    </select>
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
    mode: 'back',
    invert: 1,
  });
  camera.invert = 1;
});
</script>
