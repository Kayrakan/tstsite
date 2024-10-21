<template>
  <div>
    <div class="container-wrap container-wrap">
      <div class="inner-page">
        <section id="banner">
          <banner-video
            :title="$t('about_banner_title')"
            :cover="imgAPI.inner[1]"
            :thumb="imgAPI.photosL[53]"
            video-bg="WRCB2QSrQQU"
            video-popup="rX2T9jH0OxA"
          >
            <template #decoration>
              <parallax-deco type="scroll" />
            </template>
          </banner-video>
        </section>
        <section id="desc" :class="isMobile ? 'space-top-short' : 'space-top'">
          <description />
        </section>
        <section id="key" :class="isMobile ? 'space-top-short' : 'space-top'">
          <key-values />
        </section>
        <section id="counter" class="space-top-short">
          <counter-carousel
            :title="$t('service_counter_title')"
            :desc="$t('service_counter_desc')"
            :cover="imgAPI.photosL[32]"
          />
        </section>
        <section id="culture" :class="isMobile ? 'space-top-short' : 'space-top'">
          <culture />
        </section>
        <section id="team" class="space-top">
          <team />
        </section>
        <div :style="{ marginTop: isDesktop ? -200 + 'px' : 0 }">
          <static-gallery :btn-text="$t('btn_join')" />
        </div>
        <section id="news" :class="['space-top', { 'space=bottom-short': isMobile }]">
          <news-event />
        </section>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import { useDisplay } from 'vuetify';
import BannerVideo from '@/components/HeroBanner/MediaBanner';
import ParallaxDeco from '@/components/Parallax3d/Geometric';
import Description from '@/components/Company/About/Description';
import KeyValues from '@/components/Company/About/KeyValues';
import CounterCarousel from '@/components/Counter/CounterCarousel';
import Culture from '@/components/Company/About/Culture';
import Team from '@/components/Company/Team';
import StaticGallery from '@/components/Company/Collage/Static';
import NewsEvent from '@/components/Company/NewsEvent';
import brand from '@/assets/text/brand';
import { useHead } from '#app';
import imgAPI from '@/assets/images/imgAPI';

useHead({
  title: brand.name + ' - About',
});

const { smAndUp: isDesktop } = useDisplay();
const { smAndDown: isMobile } = useDisplay();
</script>
