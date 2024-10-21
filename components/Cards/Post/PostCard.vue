<template>
  <nuxt-link
    v-ripple
    class="post-card"
    :to="localePath(href)"
  >
    <span class="figure">
      <img :src="img" alt="post card image">
    </span>
    <span class="property">
      <span class="title" :class="small ? 'small' : 'big'">
        {{ title }}
      </span>
      <span class="desc">
        <span class="source">
          {{ source }}
        </span>
        <span>
          {{ desc }}
        </span>
      </span>
    </span>
  </nuxt-link>
</template>

<style scoped lang="scss">
@import './post-card.scss';
</style>

<script>
import { useLocalePath } from '#imports';

export default {
  props: {
    img: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    source: {
      type: String,
      required: true,
    },
    small: {
      type: Boolean,
      default: false,
    },
    desc: {
      type: String,
      required: true,
    },
    href: {
      type: String,
      default: '#',
    },
  },
  setup() {
    const localePath = useLocalePath();
    return {
      localePath,
    };
  },
};
</script>
