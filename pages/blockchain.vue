<template>
  <div>
    <nuxt-layout name="default" :home="true" prefix-menu="blockchain" :menu="singleMenu.blockchain">
      <div class="container-wrap scroll-nav-content">
        <div id="home">
          <banner-slider />
        </div>
        <section id="about" :class="isTablet ? 'space-top-short' : 'space-top'">
          <about />
        </section>
        <section id="feature" class="space-top-short">
          <feature />
        </section>
        <section id="discover" class="space-top-short">
          <step />
        </section>
        <section id="projects" :class="isMobile ? 'space-top-short' : 'space-top'">
          <projects />
        </section>
        <section id="events" :class="isMobile ? 'space-top-short' : 'space-top'">
          <event-slider />
        </section>
        <section id="event-list" class="space-top">
          <event-list />
        </section>
        <section id="blog" class="space-top-short">
          <news-event />
        </section>
        <section id="call-action" class="space-bottom-short" :class="isDesktop ? 'space-top' : 'space-top-short'">
          <call-action />
        </section>
      </div>
      <template #footer-deco>
        <footer-deco />
      </template>
      <hidden point="smDown">
        <corner prefix="blockchain" :menu="singleMenu.blockchain" />
      </hidden>
      <hidden point="mdDown">
        <notification />
      </hidden>
    </nuxt-layout>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import { useDisplay } from 'vuetify';
import BannerSlider from '@/components/HomeBlockchain/BannerSlider';
import About from '@/components/HomeBlockchain/About';
import Feature from '@/components/HomeBlockchain/Feature';
import Step from '@/components/HomeBlockchain/Step';
import Projects from '@/components/HomeBlockchain/Projects';
import EventSlider from '@/components/HomeBlockchain/EventSlider';
import EventList from '@/components/HomeBlockchain/EventList';
import CallAction from '@/components/HomeBlockchain/CallAction';
import NewsEvent from '@/components/HomeBlockchain/NewsEvent';
import singleMenu from '@/components/Header/data/single';
import FooterDeco from '@/components/Footer/Decoration/Stone';
import Hidden from '@/components/Utils/Hidden';
import Corner from '@/components/Utils/Corner';
import Notification from '@/components/Notification';
import brand from '@/assets/text/brand';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Blockchain Home Pages',
});

const { lgAndUp: isDesktop } = useDisplay();
const { mdAndDown: isTablet } = useDisplay();
const { smAndDown: isMobile } = useDisplay();

definePageMeta({
  layout: false,
});
</script>
