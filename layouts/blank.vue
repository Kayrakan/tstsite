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
          <slot />
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
