<template>
  <div>
    <div id="mainwrap" class="main-wrap mt-n16" :class="{ 'has-fixed-scroll': isTablet }">
      <main-header :menu="singleMenu.profile" />
      <main class="container-wrap container-front scroll-nav-content">
        <section id="home">
          <banner-nav :menu="singleMenu.profile" />
          <profile />
        </section>
        <section id="about" class="space-top">
          <about />
        </section>
        <section id="stats" class="space-top-short">
          <statistics />
        </section>
        <section id="portfolios">
          <portfolios />
        </section>
        <section id="testimonial" class="space-top-short">
          <testimonials />
        </section>
        <section id="pricing" :class="isTablet ? 'space-top' : 'space-top-short'">
          <pricing />
        </section>
      </main>
      <section id="contact" :class="{ 'space-top-short': isMobile }">
        <main-footer />
      </section>
      <hidden point="smDown">
        <corner prefix="avatar" :menu="singleMenu.profile" />
      </hidden>
      <hidden point="mdDown">
        <notification />
      </hidden>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import { useDisplay } from 'vuetify';
import MainHeader from '@/components/HomeCV/Header';
import BannerNav from '@/components/HomeCV/BannerNav';
import Profile from '@/components/HomeCV/Profile';
import About from '@/components/HomeCV/About';
import Statistics from '@/components/HomeCV/Statistics';
import Portfolios from '@/components/HomeCV/Portfolios';
import Testimonials from '@/components/HomeCV/Testimonials';
import Pricing from '@/components/HomeCV/Pricing';
import MainFooter from '@/components/HomeCV/Footer';
import Hidden from '@/components/Utils/Hidden';
import Corner from '@/components/Utils/Corner';
import Notification from '@/components/Notification';
import singleMenu from '@/components/Header/data/single';
import brand from '@/assets/text/brand';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Online CV',
});

const { smAndDown: isMobile } = useDisplay();
const { mdAndUp: isTablet } = useDisplay();

definePageMeta({
  layout: 'blank',
});
</script>
