<template>
  <div class="root">
    <v-avatar :image="icon" rounded="16" alt="icon" class="icon" />
    <v-card class="card">
      <figure>
        <img :src="thumb" alt="thumb">
      </figure>
    </v-card>
  </div>
</template>

<style lang="scss" scoped>
@import './preview-card.scss';
</style>

<script setup>
import { toRefs } from 'vue';

const props = defineProps({
  thumb: {
    type: String,
    required: true,
  },
  icon: {
    type: String,
    required: true,
  },
});

const { thumb, icon } = toRefs(props);
</script>
