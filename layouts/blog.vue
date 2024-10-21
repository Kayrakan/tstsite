<template>
  <div>
    <preloader />
    <theme-wrapper theme="cyber">
      <v-progress-linear
        v-model="loading"
        :active="loading < 100"
        :buffer-value="bufferValue"
        absolute
        color="primary"
        class="top-loading"
      />
      <v-app>
        <v-main>
          <div class="main-wrap">
            <blog-header />
            <div id="main-wrap" class="container-front page-enter-active" :class="{ 'page-fade-transition-exit': loading >= 100 }">
              <div class="container-front container-wrap higher-top">
                <div class="inner-page">
                  <slot />
                </div>
              </div>
            </div>
            <div id="footer" class="space-top-short">
              <main-footer />
            </div>
          </div>
        </v-main>
      </v-app>
    </theme-wrapper>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import { ref, onMounted } from 'vue';
import ThemeWrapper from '@/components/ThemeWrapper';
import BlogHeader from '@/components/Header/BlogHeader';
import MainFooter from '@/components/Footer';
import Preloader from '@/components/Preloader';

const interval = ref(0);
const loading = ref(0);
const bufferValue = ref(10);

function startBuffer() {
  clearInterval(interval.value);

  interval.value = setInterval(() => {
    loading.value += Math.random() * (15 - 5) + 5;
    bufferValue.value += Math.random() * (15 - 5) + 6;
  }, 100);
}

onMounted(() => {
  // Preloader and Progress bar setup
  startBuffer();
  setTimeout(() => {
    loading.value = 100;
    clearInterval(interval.value);
  }, 500);

  // Remove Loading Screen
  const preloader = document.getElementById('preloader');
  if (preloader !== null || undefined) {
    preloader.remove();
  }
});
</script>
