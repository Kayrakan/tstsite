<template>
  <v-card class="root">
    <a v-if="href" v-ripple :href="href">&nbsp;</a>
    <span>
      <i class="mdi" :class="icon" />
      {{ text }}
    </span>
  </v-card>
</template>

<style lang="scss" scoped>
@import './icon-card-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';

const props = defineProps({
  icon: {
    type: String,
    required: true,
  },
  text: {
    type: String,
    required: true,
  },
  href: {
    type: String,
    default: null,
  },
});

const { icon, text, href } = toRefs(props);
</script>
