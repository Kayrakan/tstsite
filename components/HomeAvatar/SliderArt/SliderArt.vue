<template>
  <div class="deco">
    <div v-if="isDesktop" class="figure" :class="{ fade: fade }">
      <slot />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './slider-art.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useDisplay } from 'vuetify';

const props = defineProps({
  fade: {
    type: Boolean,
    default: false,
  },
});

const { fade } = toRefs(props);

const { lgAndUp: isDesktop } = useDisplay();
</script>
