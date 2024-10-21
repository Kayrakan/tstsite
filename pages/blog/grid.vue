<template>
  <div>
    <nuxt-layout name="blog">
      <v-container>
        <v-row>
          <v-col cols="12" class="pa-0">
            <headline />
          </v-col>
        </v-row>
        <v-row class="mt-12 ps-3">
          <v-col md="6" cols="12" class="pe-md-8">
            <news-card
              :href="link.blogDetail"
              :img="imgAPI.photosL[37]"
              headline="Maecenas rutrum dolor sed nisi"
              title="Proin pretium arcu eget metus porta consectetur Pellentesque habitant"
              date="12 Nov 2020"
              orientation="landscape"
              type="over"
            />
          </v-col>
          <v-col md="6" cols="12">
            <news-card
              :href="link.blogDetail"
              :img="imgAPI.photosL[36]"
              headline="Maecenas rutrum dolor sed nisi"
              title="Proin pretium arcu eget metus porta consectetur Pellentesque habitant"
              date="12 Nov 2020"
              orientation="landscape"
              type="over"
            />
          </v-col>
        </v-row>
        <div class="mt-md-2">
          <v-row :class="{ 'spacing6': isTablet }">
            <v-col
              v-for="index in 12"
              :key="index"
              md="4"
              sm="6"
              cols="12"
              class="mt-15 px-3 item"
            >
              <div
                data-aos="fade-up"
                data-aos-offset="100"
                data-aos-duration="500"
                :data-aos-delay="500 + index * 100"
              >
                <news-card
                  :href="link.blogDetail"
                  :img="imgAPI.photosL[30+index]"
                  headline="Maecenas rutrum dolor sed nisi"
                  title="Proin pretium arcu eget metus porta consectetur Pellentesque habitant"
                  date="12 Nov 2020"
                  orientation="portrait"
                  type="over"
                />
              </div>
            </v-col>
          </v-row>
          <div class="arrow">
            <v-row justify="space-between" class="mt-5">
              <v-btn variant="text">
                <v-icon class="use-rtl-flip">
                  mdi-arrow-left
                </v-icon>
                {{ $t('btn_prev') }}
              </v-btn>
              <v-btn variant="text">
                {{ $t('btn_next') }}
                <v-icon class="use-rtl-flip">
                  mdi-arrow-right
                </v-icon>
              </v-btn>
            </v-row>
          </div>
        </div>
      </v-container>
    </nuxt-layout>
  </div>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/pages';
</style>

<script setup>
import { useDisplay } from 'vuetify';
import { onMounted } from 'vue';
import AOS from 'aos';
import brand from '@/assets/text/brand';
import Headline from '@/components/Company/Blog/Headline';
import NewsCard from '~/components/Cards/Post/NewsCard';
import imgAPI from '@/assets/images/imgAPI';
import link from '@/assets/text/link';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Blog Grid',
});

onMounted(() => {
  AOS.init({
    once: true,
  });
});

const { smAndUp: isTablet } = useDisplay();

definePageMeta({
  layout: false,
});
</script>
