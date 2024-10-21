<template>
  <main class="container-front container-wrap">
    <div class="inner-page">
      <section id="banner">
        <media-banner
          :title="$t('portfolio_title')"
          :cover="imgAPI.inner[19]"
          :featured="[imgAPI.photosP[27], imgAPI.photosS[12], imgAPI.photosL[54]]"
        >
          <template #decoration>
            <parallax-deco type="scroll" />
          </template>
        </media-banner>
      </section>
      <div id="gallery" :class="{ 'space-top-short': isDesktop }">
        <gallery />
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/pages';
</style>

<script setup>
import { useDisplay } from 'vuetify';
import MediaBanner from '@/components/HeroBanner/MediaBanner';
import ParallaxDeco from '@/components/Parallax3d/Ufo';
import Gallery from '@/components/Collection/Portfolio/Gallery';
import brand from '@/assets/text/brand';
import imgAPI from '@/assets/images/imgAPI';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Portfolio',
});

const { smAndUp: isDesktop } = useDisplay();
</script>
