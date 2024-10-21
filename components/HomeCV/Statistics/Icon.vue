<template>
  <div class="img">
    <img :src="img" alt="expertise">
  </div>
</template>

<style style="scss" scoped>
@import './styles/icon-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';

const props = defineProps({
  img: {
    type: String,
    required: true,
  },
});

const { img } = toRefs(props);
</script>
