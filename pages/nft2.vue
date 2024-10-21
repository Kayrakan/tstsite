<template>
  <div>
    <nuxt-layout name="default" :home="true" prefix-menu="nft2" :menu="singleMenu.nft2">
      <div class="container-wrap container-front scroll-nav-content">
        <parallax-banner v-if="isDesktop" />
        <div id="home">
          <banner-slider />
        </div>
        <section id="new" :class="{ 'space-top-short': isMobile }">
          <new-release />
        </section>
        <section id="trending" class="space-top">
          <trending />
        </section>
        <section id="rank" class="space-top">
          <table-rank />
        </section>
        <section id="explore" :class="{ 'space-top': isTablet }">
          <explore />
        </section>
        <section id="counter" :class="{ 'space-top-short': isTablet }">
          <counter />
        </section>
        <section id="auction" class="space-top-short">
          <auction />
        </section>
        <section id="sell" class="space-top-short">
          <step />
        </section>
        <section id="call-action" class="space-bottom" :class="isMobile ? 'space-top-short' : 'space-top'">
          <call-action />
        </section>
        <section id="faq" class="space-bottom-short" :class="isDesktop ? 'space-top-short' :' classes.spaceTop'">
          <faq />
        </section>
      </div>
      <template #footer-deco>
        <footer-deco />
      </template>
      <hidden point="smDown">
        <corner prefix="nft2" :menu="singleMenu.nft2" />
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
import ParallaxBanner from '@/components/HomeNFT2/Parallax/ParallaxDouble';
import BannerSlider from '@/components/HomeNFT2/BannerSlider';
import NewRelease from '@/components/HomeNFT2/NewRelease';
import Trending from '@/components/HomeNFT2/Trending';
import TableRank from '@/components/HomeNFT2/TableRank';
import Explore from '@/components/HomeNFT2/Explore';
import Counter from '@/components/HomeNFT2/Counter';
import Auction from '@/components/HomeNFT2/Auction';
import Step from '@/components/HomeNFT2/Step';
import CallAction from '@/components/HomeNFT2/CallAction';
import Faq from '@/components/HomeNFT2/Faq';
import singleMenu from '@/components/Header/data/single';
import FooterDeco from '@/components/Footer/Decoration/Fog';
import Hidden from '@/components/Utils/Hidden';
import Corner from '@/components/Utils/Corner';
import Notification from '@/components/Notification';
import brand from '@/assets/text/brand';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - NFT 2 Marketplace',
});

const { lgAndUp: isDesktop } = useDisplay();
const { lgAndDown: isTablet } = useDisplay();
const { smAndDown: isMobile } = useDisplay();

definePageMeta({
  layout: false,
});
</script>
