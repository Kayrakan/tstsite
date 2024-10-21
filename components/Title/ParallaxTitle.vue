<template>
  <div
    class="parallax-title"
    :style="{ 'padding-top': (transform - offset) + 'px' }"
  >
    <h2
      ref="decoTitle"
      class="deco-title"
      :class="'use-text-grd-' + color"
      :style="{ opacity: transform > 30 ? transform / 300 : 0.15 }"
    >
      {{ bgTitle }}
    </h2>
    <title-main align="center" :text="mainTitle" />
  </div>
</template>

<style lang="scss" scoped>
@import './parallax-title-style';
</style>

<script setup>
import { ref, onMounted, toRefs } from 'vue';
import TitleMain from './Title';

const offset = 24;
const decoTitle = ref(null);
const transform = ref(offset);

const props = defineProps({
  mainTitle: {
    type: String,
    required: true,
  },
  bgTitle: {
    type: String,
    required: true,
  },
  color: {
    type: String,
    default: 'double-main',
  },
});

const { mainTitle, bgTitle, color } = toRefs(props);

function handleScroll(event, divider) {
  if (decoTitle.value) {
    const coordinat = decoTitle.value.getBoundingClientRect();
    if (coordinat.top > 0) {
      transform.value = coordinat.top / divider;
    } else {
      transform.value = offset;
    }
  }
}

onMounted(() => {
  const divider = window.innerWidth > 600 ? 1.5 : 3;
  window.addEventListener('scroll', (e) => handleScroll(e, divider));
});

</script>
