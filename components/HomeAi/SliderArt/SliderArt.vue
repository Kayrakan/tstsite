<template>
  <div class="deco">
    <div class="figure" :class="{fade: fade}">
      <slot />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './slider-art-style';
</style>

<script setup>
import { toRefs } from 'vue';

const props = defineProps({
  fade: {
    type: Boolean,
    default: false,
  },
});

const { fade } = toRefs(props);
</script>
