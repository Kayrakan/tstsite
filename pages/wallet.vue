<template>
  <div>
    <nuxt-layout name="default" :home="true" prefix-menu="wallet" :menu="singleMenu.wallet">
      <div class="container-wrap container-front scroll-nav-content">
        <div id="home">
          <banner-slider />
        </div>
        <section id="howto" class="space-top">
          <step />
        </section>
        <section id="chart" :class="isMobile ? 'space-top-short' : 'space-top'">
          <chart-price />
        </section>
        <section id="feature" :class="isMobile ? 'space-top-short' : 'space-top'">
          <feature />
        </section>
        <section id="discover" class="space-top">
          <benefit />
        </section>
        <section id="security" class="space-top-short">
          <security />
        </section>
        <section id="community" :class="{ 'space-top': !isMobile }">
          <counter />
        </section>
        <section id="testimonials" class="space-top-short">
          <testimonials />
        </section>
        <section id="call-action" class="space-bottom" :class="isMobile ? 'space-top-short' : 'space-top'">
          <call-action />
        </section>
      </div>
      <template #footer-deco>
        <footer-deco />
      </template>
      <hidden point="smDown">
        <corner prefix="blockchain" :menu="singleMenu.wallet" />
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
import BannerSlider from '@/components/HomeWallet/BannerSlider';
import Step from '@/components/HomeWallet/Step';
import ChartPrice from '@/components/HomeWallet/ChartPrice';
import Feature from '@/components/HomeWallet/Feature';
import Benefit from '@/components/HomeWallet/Benefit';
import Security from '@/components/HomeWallet/Security';
import Counter from '@/components/HomeWallet/Counter';
import Testimonials from '@/components/HomeWallet/Testimonials';
import CallAction from '@/components/HomeWallet/CallAction';
import singleMenu from '@/components/Header/data/single';
import FooterDeco from '@/components/Footer/Decoration/Line';
import Hidden from '@/components/Utils/Hidden';
import Corner from '@/components/Utils/Corner';
import Notification from '@/components/Notification';
import brand from '@/assets/text/brand';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Crypto Wallet Home Pages',
});

const { smAndDown: isMobile } = useDisplay();

definePageMeta({
  layout: false,
});
</script>
