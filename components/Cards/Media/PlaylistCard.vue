<template>
  <nuxt-link
    v-ripple
    draggable="false"
    class="playlist-card"
    :class="[{ deco: withDeco }, bgcolor]"
    :to="localePath(href)"
  >
    <span v-if="img" class="figure">
      <img :src="img" alt="img">
    </span>
    <span
      class="property text-center"
      :class="[color, { 'text-center': textCenter }]"
    >
      <span class="head" :class="textCenter ? 'justify-center' : 'justify-start'">
        <span v-if="logo" class="logo">
          <img :src="logo" alt="logo">
        </span>
        <span class="text">
          <span class="title">
            {{ title }}
            <v-icon v-if="verifiedItem" class="verified">mdi-check-decagram</v-icon>
          </span>
          <span v-if="name" class="user">
            By&nbsp;
            <span class="avatar">
              <img :src="avatar" alt="logo">
            </span>
            <span class="name">
              {{ name }}
            </span>
            <v-icon v-if="verifiedItem" class="verified">mdi-check-decagram</v-icon>
          </span>
        </span>
      </span>
      <span class="desc">
        {{ desc }}
      </span>
      <ul class="gallery">
        <li v-for="(item, index) in items" :key="index">
          <img :src="item" alt="media">
          <span v-if="index === items.length - 1">
            <v-icon>mdi-view-quilt</v-icon>
            {{ count }}
          </span>
        </li>
      </ul>
    </span>
  </nuxt-link>
</template>

<style lang="scss" scoped>
@import './playlist-card.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const props = defineProps({
  bgcolor: {
    type: String,
    default: 'primary-light',
  },
  img: {
    type: String,
    default: null,
  },
  avatar: {
    type: String,
    default: '/',
  },
  logo: {
    type: String,
    default: null,
  },
  title: {
    type: String,
    required: true,
  },
  verifiedItem: {
    type: Boolean,
    default: false,
  },
  name: {
    type: String,
    default: null,
  },
  desc: {
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
  count: {
    type: String,
    required: true,
  },
  items: {
    type: Array,
    required: true,
  },
  withDeco: {
    type: Boolean,
    default: false,
  },
  textCenter: {
    type: Boolean,
    required: false,
  },
});

const {
  bgcolor, img, avatar,
  logo, title,
  verifiedItem, name, desc,
  color, href, count,
  items, withDeco, textCenter,
} = toRefs(props);

const localePath = useLocalePath();
</script>
