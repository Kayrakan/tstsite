<template>
  <div>
    <nuxt-layout name="default" :home="true" :menu="singleMenu.ai">
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
        <section id="discover" :class="isMobile ? 'space-top-short' : 'space-top'">
          <research />
        </section>
        <section id="community" :class="isMobile ? 'space-top-short' : 'space-top'">
          <community />
        </section>
        <section id="faq" class="space-top-short">
          <faq />
        </section>
        <section id="blog" class="space-top-short">
          <news-event />
        </section>
        <section id="call-action" class="space-bottom-short" :class="isTablet ? 'space-top-short' : 'space-top'">
          <call-action />
        </section>
      </div>
      <template #footer-deco>
        <footer-deco />
      </template>
      <hidden point="smDown">
        <corner :menu="singleMenu.ai" />
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
import { onMounted } from 'vue';
import { useI18n } from 'vue-i18n';
import { useDisplay } from 'vuetify';
import BannerSlider from '@/components/HomeAi/BannerSlider';
import About from '@/components/HomeAi/About';
import Feature from '@/components/HomeAi/Feature';
import Research from '@/components/HomeAi/Research';
import Step from '@/components/HomeAi/Step';
import Community from '@/components/HomeAi/Community';
import Faq from '@/components/HomeAi/Faq';
import NewsEvent from '@/components/HomeAi/NewsEvent';
import CallAction from '@/components/HomeAi/CallAction';
import singleMenu from '@/components/Header/data/single';
import FooterDeco from '@/components/Footer/Decoration/Liquid';
import Hidden from '@/components/Utils/Hidden';
import Corner from '@/components/Utils/Corner';
import Notification from '@/components/Notification';
import brand from '@/assets/text/brand';
import { useHead, useRouter, useCookie } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - AI Home Pages',
});

// push route to the stored cookie languages only for index page
const router = useRouter();
const storedLang = useCookie('i18n_redirected');
const i18nLocale = useI18n();

const { mdAndDown: isTablet } = useDisplay();
const { smAndDown: isMobile } = useDisplay();

const defaultLocale = '/' + i18nLocale.fallbackLocale.value;
onMounted(() => {
  const rootUrl = document.location.pathname === '/' || document.location.pathname === defaultLocale;
  if (storedLang.value && rootUrl) {
    router.push({ path: `/${storedLang.value}` });
  }
});

definePageMeta({
  layout: false,
});
</script>
