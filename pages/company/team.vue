<template>
  <div>
    <div class="container-wrap container-wrap">
      <div class="inner-page">
        <section id="banner">
          <basic-banner
            :bg-title="$t('team_bgtitle')"
            :title="$t('team_title')"
            :desc="$t('team_desc')"
          >
            <template #decoration>
              <parallax-deco type="scroll" />
            </template>
          </basic-banner>
        </section>
        <div>
          <carousel-gallery overlap />
        </div>
        <section id="team" class="space-top-short">
          <team bg="parallax" />
        </section>
        <call-action />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import BasicBanner from '@/components/HeroBanner/BasicBanner';
import ParallaxDeco from '@/components/Parallax3d/Flower';
import CarouselGallery from '@/components/Company/Collage/Carousel';
import Team from '@/components/Company/Team';
import CallAction from '~/components/Company/CallAction';
import brand from '@/assets/text/brand';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Team',
});
</script>
