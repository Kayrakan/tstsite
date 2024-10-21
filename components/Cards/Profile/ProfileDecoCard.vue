<template>
  <div :class="size" class="profile-card">
    <div class="avatar">
      <template v-if="size === 'big'">
        <svg class="primary">
          <use xlink:href="/images/decoration/deco-liquid-line.svg#main" />
        </svg>
        <svg class="secondary">
          <use xlink:href="/images/decoration/deco-liquid-line.svg#main" />
        </svg>
      </template>
      <template v-if="size === 'medium'">
        <svg class="primary">
          <use xlink:href="/images/decoration/deco-leaf-line.svg#main" />
        </svg>
        <svg class="secondary">
          <use xlink:href="/images/decoration/deco-leaf-line.svg#main" />
        </svg>
      </template>
      <span v-if="size === 'small'" class="deco-circle" />
      <div v-else class="bg">
        <span />
      </div>
      <figure>
        <img :src="avatar" alt="avatar">
      </figure>
    </div>
    <div class="property">
      <h1>{{ name }}</h1>
      <h3>{{ title }}</h3>
      <p>{{ desc }}</p>
      <div class="socmed">
        <v-btn v-for="(item, index) in socmed" :key="index" variant="text" icon size="large">
          <i :class="'ion-logo-'+item" />
        </v-btn>
      </div>
    </div>
    <nuxt-link v-if="href" v-ripple class="link" :to="localePath(href)" />
  </div>
</template>

<style lang="scss" scoped>
@import './profile-deco-card';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const localePath = useLocalePath();

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  avatar: {
    type: String,
    required: true,
  },
  size: {
    type: String,
    default: 'medium',
  },
  href: {
    type: String,
    default: null,
  },
  desc: {
    type: String,
    default: null,
  },
  socmed: {
    type: Array,
    default: null,
  },
});

const {
  size, name, title,
  avatar, socmed, desc,
  href,
} = toRefs(props);
</script>
