<template>
  <div>
    <nuxt-layout name="default" :home="true" :subscribe="true" prefix-menu="fintech" :menu="singleMenu.fintech">
      <div class="container-wrap container-front scroll-nav-content">
        <div id="home">
          <banner-slider />
        </div>
        <section id="howto" class="space-top container-front">
          <step />
        </section>
        <section id="chart" class="space-top">
          <chart-price />
        </section>
        <section id="feature" :class="{ 'space-top-short' : isTablet }">
          <feature />
        </section>
        <section id="benefit" class="space-top">
          <benefit />
        </section>
        <section id="counter">
          <counter />
        </section>
        <section id="merchants" class="space-top-short">
          <merchants />
        </section>
        <section id="call-action" class="space-top space-bottom">
          <call-action />
        </section>
        <section id="call-action" class="space-top-short">
          <faq />
        </section>
      </div>
      <template #footer-deco>
        <footer-deco />
      </template>
      <hidden point="smDown">
        <corner prefix="blockchain" :menu="singleMenu.fintech" />
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
import BannerSlider from '@/components/HomeFintech/BannerSlider';
import Step from '@/components/HomeFintech/Step';
import ChartPrice from '@/components/HomeFintech/ChartPrice';
import Feature from '@/components/HomeFintech/Feature';
import Benefit from '@/components/HomeFintech/Benefit';
import Counter from '@/components/HomeFintech/Counter';
import Merchants from '@/components/HomeFintech/Merchants';
import Faq from '@/components/HomeFintech/Faq';
import CallAction from '@/components/HomeFintech/CallAction';
import singleMenu from '@/components/Header/data/single';
import FooterDeco from '@/components/Footer/Decoration/Wave';
import Hidden from '@/components/Utils/Hidden';
import Corner from '@/components/Utils/Corner';
import Notification from '@/components/Notification';
import brand from '@/assets/text/brand';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Fintech Home Pages',
});

const { lgAndDown: isTablet } = useDisplay();

definePageMeta({
  layout: false,
});
</script>
