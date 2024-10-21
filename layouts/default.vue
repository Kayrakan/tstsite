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
            <main-header :home="home" :menu="menu" :prefix="prefix" />
            <div id="main-wrap" class="container-front page-enter-active" :class="{ 'page-fade-transition-exit': loading >= 100 }">
              <slot />
            </div>
            <div v-if="$slots['footer-deco']">
              <slot name="footer-deco" />
            </div>
            <div v-else>
              <footer-deco>
                <div id="footer_deco" />
              </footer-deco>
            </div>
            <Teleport v-if="loaded" to="#footer_deco">
              <div>
                <section v-if="subscribe" id="subscribe" class="space-bottom-short">
                  <subscribe-form />
                </section>
                <main-footer />
              </div>
            </Teleport>
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
import singleMenu from '@/components/Header/data/single';
import ThemeWrapper from '@/components/ThemeWrapper';
import Preloader from '@/components/Preloader';
import MainHeader from '@/components/Header';
import SubscribeForm from '@/components/SubscribeForm';
import FooterDeco from '@/components/Footer/Decoration/General';
import MainFooter from '@/components/Footer';

const interval = ref(0);
const loading = ref(0);
const bufferValue = ref(10);
const loaded = ref(false);
const layoutProps = useAttrs();

const home = layoutProps.home ?? false;
const menu = layoutProps.menu ?? singleMenu.inner;
const prefix = layoutProps['prefix-menu'] ?? 'ai-landing';
const subscribe = layoutProps.subscribe ?? false;

function startBuffer() {
  clearInterval(interval.value);

  interval.value = setInterval(() => {
    loading.value += Math.random() * (15 - 5) + 5;
    bufferValue.value += Math.random() * (15 - 5) + 6;
  }, 100);
}

onMounted(() => {
  loaded.value = true;

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
