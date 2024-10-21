<template>
  <div>
    <blur-gradient />
    <div class="container-general container-front">
      <pricing-group-card />
      <div class="space-top space-bottom-short">
        <faq />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import BlurGradient from '@/components/Artworks/BlurGradient';
import PricingGroupCard from '@/components/Cards/Pricing/PricingGroupCard';
import Faq from '@/components/Utils/Faq';
import brand from '@/assets/text/brand';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Pricing',
});
</script>
