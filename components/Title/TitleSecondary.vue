<template>
  <div class="title-secondary" :class="[color, align]">
    <h4>{{ text }}</h4>
  </div>
</template>

<style lang="scss" scoped>
@import './title-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';

const props = defineProps({
  align: {
    type: String,
    default: 'left',
  },
  text: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    default: 'primary',
  },
});

const { text, align, color } = toRefs(props);
</script>
