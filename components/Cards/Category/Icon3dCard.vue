<template>
  <nuxt-link
    v-ripple
    draggable="false"
    class="category-card"
    :class="color"
    :to="localePath(href)"
  >
    <span class="icons">
      <icons3d :color="color" :icon="icon" />
    </span>
    <span component="span" class="title">
      {{ title }}
    </span>
  </nuxt-link>
</template>

<style lang="scss" scoped>
@import './icon3d-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';
import Icons3d from '../../Icons3d';

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  icon: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    default: 'purple',
  },
  href: {
    type: String,
    default: '#',
  },
});

const {
  color, title,
  icon, href,
} = toRefs(props);

const localePath = useLocalePath();
</script>
