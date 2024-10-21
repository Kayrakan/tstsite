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
            <main-header :href="hrefLink" :text="textLink" />
            <div id="main-wrap" class="container-front page-enter-active" :class="{ 'page-fade-transition-exit': loading >= 100 }">
              <slot />
            </div>
            <footer-deco>
              <main-footer />
            </footer-deco>
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
import { ref, onMounted, useAttrs } from 'vue';
import ThemeWrapper from '@/components/ThemeWrapper';
import MainHeader from '@/components/Header/Basic';
import MainFooter from '@/components/Footer';
import FooterDeco from '@/components/Footer/Decoration/General';
import Preloader from '@/components/Preloader';
import link from '@/assets/text/link';

const interval = ref(0);
const loading = ref(0);
const bufferValue = ref(10);
const layoutProps = useAttrs();

const hrefLink = layoutProps.link ?? link.register;
const textLink = layoutProps.textLink ?? 'register';

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
