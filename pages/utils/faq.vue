<template>
  <div>
    <blur-gradient />
    <div class="inner-wrap">
      <div class="container-wrap">
        <div class="container-general">
          <div id="banner" class="space-bottom-short">
            <basic-banner
              :title="$t('faq_title')"
              :desc="$t('contact_subtitle')"
              :bg-title="$t('header_faq')"
            >
              <template #decoration>
                <parallax-deco type="scroll" />
              </template>
            </basic-banner>
            <div class="mt-n15">
              <br>
              <div class="mt-n15">
                <br>
                <div class="mt-md-n15">
                  <v-container class="max-md container-front">
                    <search v-model="keyword" />
                  </v-container>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="space-bottom-short">
          <shortcut />
        </div>
        <v-container class="space-bottom-short">
          <v-row justify="center">
            <v-col class="px-6" lg="4" md="4" cols="12" :order="isMobile ? 'last' : 'first'">
              <div :class="{ 'px-3': !isTablet}">
                <topic-list />
                <helper-widget />
              </div>
            </v-col>
            <v-col class="px-sm-10" lg="7" md="7" cols="12" :order="isMobile ? 'first' : 'last'">
              <faq-list />
            </v-col>
          </v-row>
        </v-container>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import { ref } from 'vue';
import { useDisplay } from 'vuetify';
import BlurGradient from '@/components/Artworks/BlurGradient';
import ParallaxDeco from '@/components/Parallax3d/Food';
import BasicBanner from '@/components/HeroBanner/BasicBanner';
import Search from '@/components/Filter/Search';
import FaqList from '@/components/Utils/Faq/FaqList';
import Shortcut from '@/components/Utils/Faq/Shortcut';
import TopicList from '@/components/Utils/Faq/TopicList';
import HelperWidget from '@/components/Utils/Faq/HelperWidget';
import brand from '@/assets/text/brand';
import { useHead } from '#app';

useHead({
  title: brand.name + ' - Faq',
});

const { mdAndDown: isMobile } = useDisplay();
const { md: isTablet } = useDisplay();

const keyword = ref('');
</script>
