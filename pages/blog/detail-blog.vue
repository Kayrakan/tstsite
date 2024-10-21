<template>
  <div>
    <nuxt-layout name="blog">
      <blue-gradient />
      <div class="space-bottom-short">
        <v-container>
          <v-row>
            <v-col md="8" cols="12" class="py-0">
              <article-blog />
            </v-col>
            <v-col md="4" cols="12">
              <sidebar />
            </v-col>
          </v-row>
        </v-container>
      </div>
    </nuxt-layout>
  </div>
</template>

<style lang="scss" scoped>
@import '@/assets/scss/pages';
</style>

<script setup>
import brand from '@/assets/text/brand';
import BlueGradient from '@/components/Artworks/BlurGradient';
import ArticleBlog from '@/components/Company/Blog/Article';
import Sidebar from '@/components/Company/Blog/Sidebar';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Blog Detail',
});

definePageMeta({
  layout: false,
});
</script>
