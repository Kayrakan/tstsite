<template>
  <v-btn size="large" :to="localePath(href)" class="btn-large" :class="{ 'full-height': fullHeight }">
    <img src="/images/inner/fog.png" alt="background">
    <span class="deco">
      <span />
      <span />
      <span />
    </span>
    <h2>{{ text }}</h2>
    <v-icon class="icon">
      mdi-arrow-right
    </v-icon>
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
  fullHeight: {
    type: Boolean,
    default: false,
  },
  href: {
    type: String,
    default: '#',
  },
});

const { text, fullHeight, href } = toRefs(props);
</script>
