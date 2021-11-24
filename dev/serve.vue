<script lang="ts">
import { defineComponent } from "vue";
import ConfettiExplosion from "@/ConfettiExplosion.vue";

export default defineComponent({
  name: "ServeDev",
  components: {
    ConfettiExplosion,
  },
});
</script>

<template>
  <div id="app">
    <ConfettiExplosion />
  </div>
</template>

<style>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
