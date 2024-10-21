<template>
  <v-btn
    :class="orientation"
    :to="localePath(href)"
    class="case-card"
    draggable="false"
  >
    <span class="figure">
      <img :src="bg" alt="img">
    </span>
    <span class="property">
      <span class="title">
        <span class="logo">
          <img :src="logo" alt="logo">
        </span>
        <span class="text">
          <span class="title">
            {{ title }}
          </span>
          <span class="desc">
            {{ desc }}
          </span>
        </span>
      </span>
    </span>
  </v-btn>
</template>

<style lang="scss" scoped>
@import './case-card.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const props = defineProps({
  bg: {
    type: String,
    default: '',
  },
  logo: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  desc: {
    type: String,
    required: true,
  },
  href: {
    type: String,
    required: true,
  },
  orientation: {
    type: String,
    default: 'portrait',
  },
});

const {
  bg, logo, title,
  desc, href, orientation,
} = toRefs(props);

const localePath = useLocalePath();
</script>
