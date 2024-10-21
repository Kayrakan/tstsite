<template>
  <div class="container-front container-wrap">
    <div class="inner-page">
      <section id="banner">
        <banner-image
          :title="$t('service_banner_title')"
          :cover="imgAPI.inner[2]"
        >
          <template #decoration>
            <parallax-deco type="scroll" />
          </template>
        </banner-image>
      </section>
      <section id="group" :class="isTablet ? 'space-top' : 'space-top-short'">
        <group />
      </section>
      <section id="single" class="space-top">
        <single />
      </section>
      <section id="counter" class="space-top-short">
        <counter-carousel
          :title="$t('service_counter_title')"
          :desc="$t('service_counter_desc')"
          :cover="imgAPI.photosL[32]"
        />
      </section>
      <section id="values" :class="isTablet ? 'space-top-short' : 'space-top'">
        <values />
      </section>
      <section id="related" :class="[isDesktop ? 'space-top-short' : 'space-top']" class="space-bottom-short">
        <related />
      </section>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import { useDisplay } from 'vuetify';
import BannerImage from '@/components/HeroBanner/MediaBanner';
import ParallaxDeco from '@/components/Parallax3d/Snail';
import Group from '@/components/Collection/Services/Group';
import Single from '@/components/Collection/Services/Single';
import CounterCarousel from '@/components/Counter/CounterCarousel';
import Values from '@/components/Collection/Services/Values';
import Related from '@/components/Collection/Services/Related';
import brand from '@/assets/text/brand';
import imgAPI from '@/assets/images/imgAPI';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Services',
});

const { lgAndUp: isDesktop } = useDisplay();
const { smAndUp: isTablet } = useDisplay();
</script>
