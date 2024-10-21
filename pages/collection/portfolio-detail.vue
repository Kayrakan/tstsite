<template>
  <div>
    <main class="container-front container-wrap">
      <div class="inner-page">
        <section id="banner">
          <media-banner
            title="Interdum et Malesuada Fames"
            :cover="imgAPI.photosL[43]"
            :thumb="imgAPI.photosP[5]"
            :tags="['branding', 'creative']"
          >
            <template #decoration>
              <parallax-deco type="scroll" />
            </template>
          </media-banner>
        </section>
        <section id="content">
          <v-container class="px-0">
            <v-row justify="center">
              <v-col lg="7" md="8" cols="12">
                <detail />
              </v-col>
              <v-col lg="5" md="4" sm="8" cols="12">
                <sidebar />
              </v-col>
            </v-row>
          </v-container>
        </section>
      </div>
    </main>
  </div>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/pages';
</style>

<script setup>
import MediaBanner from '@/components/HeroBanner/MediaBanner';
import ParallaxDeco from '@/components/Parallax3d/Basket';
import Sidebar from '@/components/Collection/Portfolio/Sidebar';
import Detail from '@/components/Collection/Portfolio/Detail';
import brand from '@/assets/text/brand';
import imgAPI from '@/assets/images/imgAPI';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Portfolio Detail',
});
</script>
