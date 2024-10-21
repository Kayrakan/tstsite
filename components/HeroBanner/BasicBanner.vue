<template>
  <slot name="decoration" />
  <v-container>
    <div class="basic-hero">
      <background-title
        :bg-title="bgTitle"
        :main-title="title"
        :color="currentTheme === 'dark' ? 'triple-dark' : 'triple-light'"
      />
      <p class="px-md-10">
        {{ desc }}
      </p>
      <div v-if="btnPrimary || btnSecondary" class="btn-area-simple">
        <v-btn
          v-if="btnPrimary"
          :to="localePath(link1)"
          color="primary"
          size="large"
        >
          {{ btnPrimary }}
        </v-btn>
        <v-btn
          v-if="btnSecondary"
          :to="localePath(link2)"
          variant="outlined"
          :color="currentTheme === 'dark' ? 'white' : 'black'"
          size="large"
        >
          {{ btnSecondary }}
        </v-btn>
      </div>
    </div>
  </v-container>
</template>

<style lang="scss" scoped>
@import "./hero-style.scss";
</style>

<script setup>
import { toRefs } from 'vue';
import { useTheme } from 'vuetify';
import { useLocalePath } from '#imports';
import BackgroundTitle from '../Title/BgTitle';

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  bgTitle: {
    type: String,
    required: true,
  },
  desc: {
    type: String,
    required: true,
  },
  btnPrimary: {
    type: String,
    default: null,
  },
  btnSecondary: {
    type: String,
    default: null,
  },
  link1: {
    type: String,
    default: '#',
  },
  link2: {
    type: String,
    default: '#',
  },
});

const {
  title, bgTitle, desc,
  btnPrimary, btnSecondary,
  link1, link2,
} = toRefs(props);

const localePath = useLocalePath();
const { name: currentTheme } = useTheme();
</script>
