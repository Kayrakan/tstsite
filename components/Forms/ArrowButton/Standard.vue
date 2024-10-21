<template>
  <v-btn :size="size" :to="localePath(href)" class="btn-standard" :class="color">
    {{ text }}
    <v-icon>mdi-arrow-right</v-icon>
  </v-btn>
</template>

<style lang="scss" scoped>
@import './arrow-button-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const localePath = useLocalePath();

const props = defineProps({
  text: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    default: 'primary',
  },
  href: {
    type: String,
    default: '#',
  },
  size: {
    type: String,
    default: 'large',
  },
});

const { text, color, href } = toRefs(props);
</script>
