<template>
  <nuxt-link
    v-ripple
    draggable="false"
    class="category-card"
    :to="localePath(href)"
  >
    <span class="images" :class="color">
      <span
        v-for="(item, index) in images"
        :key="index"
        :class="{ center: index === 1 }"
        class="figure"
      >
        <img :src="item" alt="collection preview">
      </span>
    </span>
    <span class="title">
      {{ title }}
    </span>
  </nuxt-link>
</template>

<style lang="scss" scoped>
@import './img-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const props = defineProps({
  color: {
    type: String,
    default: 'purple',
  },
  title: {
    type: String,
    required: true,
  },
  href: {
    type: String,
    default: '#',
  },
  images: {
    type: Array,
    required: true,
  },
});

const {
  color, title,
  href, images,
} = toRefs(props);

const localePath = useLocalePath();
</script>
