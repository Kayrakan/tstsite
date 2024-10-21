<template>
  <v-card class="card" :class="color">
    <nuxt-link v-ripple :to="localePath(href)">
&nbsp;
    </nuxt-link>
    <div class="content" :class="{ bordered: bordered }">
      <div class="text">
        <h3>{{ title }}</h3>
        <p>{{ desc }}</p>
      </div>
      <img :src="img" alt="illustration">
    </div>
  </v-card>
</template>

<style lang="scss" scoped>
@import './single-card-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  desc: {
    type: String,
    required: true,
  },
  bordered: {
    type: Boolean,
    default: false,
  },
  img: {
    type: String,
    default: null,
  },
  color: {
    type: String,
    default: 'primary',
  },
  href: {
    type: String,
    default: '#',
  },
});

const {
  title, desc, color,
  img, bordered, href,
} = toRefs(props);

const localePath = useLocalePath();
</script>
