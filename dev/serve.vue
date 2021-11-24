<script setup lang="ts">
import { nextTick, ref } from "vue";
import ConfettiExplosion from "@/ConfettiExplosion.vue";

const visible = ref(false);
const explode = async () => {
  visible.value = false;
  await nextTick();
  visible.value = true;
};
</script>

<template>
  <div id="app">
    <button @click="explode">Show confetti</button>
    <ConfettiExplosion v-if="visible" />
  </div>
</template>

<style>
html,
body {
  height: 100%;
}
#app {
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
