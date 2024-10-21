<template>
  <div>
    <div class="container-wrap container-wrap">
      <div class="inner-page">
        <section id="banner">
          <basic-banner
            :bg-title="$t('career_bgtitle')"
            :title="$t('career_title')"
            :desc="$t('career_subtitle')"
            :btn-primary="$t('career_joblist')"
            :btn-secondary="$t('about_bgtitle')"
            link1="#joblist"
            :link2="link.about"
          >
            <template #decoration>
              <parallax-deco type="scroll" />
            </template>
          </basic-banner>
        </section>
        <div>
          <static-gallery overlap />
        </div>
        <section id="benefit" :class="{ 'space-top': isTablet }">
          <benefit />
        </section>
        <section id="joblist" class="space-top-short">
          <job-list />
        </section>
        <section id="news" :class="isDesktop ? 'space-top-short' : 'space-top'">
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
import BasicBanner from '@/components/HeroBanner/BasicBanner';
import ParallaxDeco from '@/components/Parallax3d/Planet';
import StaticGallery from '@/components/Company/Collage/Static';
import Benefit from '@/components/Company/Career/Benefit';
import JobList from '@/components/Company/Career/JobList';
import NewsEvent from '@/components/Company/NewsEvent';
import brand from '@/assets/text/brand';
import link from '@/assets/text/link';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Career',
});

const { mdAndUp: isDesktop } = useDisplay();
const { smAndUp: isTablet } = useDisplay();
</script>
