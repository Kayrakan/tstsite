<template>
  <v-card class="icon-card">
    <div class="icon">
      <icons3d :icon="icon" :color="color" />
    </div>
  </v-card>
</template>

<style style="scss" scoped>
@import './styles/icon-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import Icons3d from '../../Icons3d';

const props = defineProps({
  icon: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    required: true,
  },
});

const { icon, color } = toRefs(props);
</script>
