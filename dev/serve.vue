<script lang="ts">
import { defineComponent } from 'vue';
import ConfettiExplosion from '@/confetti-explosion.vue';

export default defineComponent({
  name: 'ServeDev',
  components: {
    ConfettiExplosion
  }
});
</script>

<template>
  <div id="app">
    <confetti-explosion />
  </div>
</template>
