<template>
  <v-card class="card" :class="[color, { 'with-img': img }]">
    <nuxt-link v-ripple :to="localePath(href)">
&nbsp;
    </nuxt-link>
    <div class="content" :class="type">
      <div class="text">
        <h3>{{ title }}</h3>
        <p>{{ desc }}</p>
      </div>
      <img v-if="img" :class="align" :src="img" alt="illustration">
      <div class="group" :class="align">
        <div class="items" :class="[{ medium: items.length > 4 }, { 'full-width': items.length < 3 && isDesktop }]">
          <div v-for="(item, index) in items" :key="index" class="item" :class="{ darken: darken }">
            <i :class="['mdi', item.icon, 'use-text-'+itemColor]" />
            {{ item.name }}
          </div>
        </div>
      </div>
    </div>
  </v-card>
</template>

<style lang="scss" scoped>
@import './group-card-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useDisplay } from 'vuetify';
import { useLocalePath } from '#imports';

const { mdAndUp: isDesktop } = useDisplay();

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  desc: {
    type: String,
    required: true,
  },
  items: {
    type: Array,
    required: true,
  },
  darken: {
    type: Boolean,
    default: false,
  },
  img: {
    type: String,
    default: null,
  },
  align: {
    type: String,
    default: 'left',
  },
  color: {
    type: String,
    default: 'primary',
  },
  itemColor: {
    type: String,
    default: 'white',
  },
  type: {
    type: String,
    default: 'compact',
  },
  href: {
    type: String,
    default: '#',
  },
});

const {
  title, desc, color,
  img, items, type,
  itemColor, href, darken,
  align,
} = toRefs(props);

const localePath = useLocalePath();

</script>
