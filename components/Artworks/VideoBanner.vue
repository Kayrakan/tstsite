<template>
  <div class="root">
    <v-btn
      v-if="action"
      class="play-btn"
      color="secondary"
      icon="mdi-play"
      variant="flat"
      size="x-large"
      @click="action"
    />
    <div class="video">
      <div class="cover">
        <img :src="cover" alt="cover">
      </div>
      <span class="top-left">
        <img :src="topLeft" alt="app">
      </span>
      <span class="top-right">
        <img :src="topRight" alt="app">
      </span>
      <span class="bottom-left">
        <img :src="bottomLeft" alt="app">
      </span>
      <span class="bottom-right">
        <img :src="bottomRight" alt="app">
      </span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './video-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';

const props = defineProps({
  cover: {
    type: String,
    required: true,
  },
  topLeft: {
    type: String,
    required: true,
  },
  topRight: {
    type: String,
    required: true,
  },
  bottomLeft: {
    type: String,
    required: true,
  },
  bottomRight: {
    type: String,
    required: true,
  },
  action: {
    type: Function,
    default: null,
  },
});

const {
  cover, topLeft, topRight,
  bottomLeft, bottomRight, action,
} = toRefs(props);
</script>
