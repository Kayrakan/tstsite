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
        <div class="mt-sm-10 ps-3">
          <v-row :class="{ spacing6: isTablet }">
            <v-col md="8" cols="12">
              <div
                v-for="index in 12"
                :key="index"
                :class="{ 'mt-lg-15 mt-8': index > 1 }"
              >
                <news-card
                  :href="link.blogDetail"
                  :img="imgAPI.photosL[30+index]"
                  headline="Maecenas rutrum dolor sed nisi"
                  title="Proin pretium arcu eget metus porta consectetur Pellentesque habitant"
                  date="12 Nov 2020"
                  orientation="landscape"
                  type="over"
                />
              </div>
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
            </v-col>
            <v-col md="4" cols="12">
              <sidebar />
            </v-col>
          </v-row>
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
import brand from '@/assets/text/brand';
import Headline from '@/components/Company/Blog/Headline';
import Sidebar from '@/components/Company/Blog/Sidebar';
import NewsCard from '~/components/Cards/Post/NewsCard';
import imgAPI from '@/assets/images/imgAPI';
import link from '@/assets/text/link';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

const { smAndUp: isTablet } = useDisplay();

useHead({
  title: brand.name + ' - Blog Home',
});

definePageMeta({
  layout: false,
});
</script>
