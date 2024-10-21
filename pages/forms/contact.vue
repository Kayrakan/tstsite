<template>
  <div>
    <blur-gradient />
    <contact />
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import brand from '@/assets/text/brand';
import BlurGradient from '@/components/Artworks/BlurGradient';
import Contact from '@/components/Forms/Contact';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Contact',
});
</script>
