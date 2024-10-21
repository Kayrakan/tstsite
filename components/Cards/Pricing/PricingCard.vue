<template>
  <div class="pricing-card" :class="color">
    <v-card>
      <v-card-title class="card-header">
        {{ title }}
      </v-card-title>
      <div class="card-pricing">
        <h2 class="use-text-title">
          $
          {{ price }}
        </h2>
        <h3 v-if="per !== ''">
          / {{ per }}
        </h3>
      </div>
      <p class="text-center desc">
        {{ description }}
      </p>
      <v-card-text class="card-content">
        <ul>
          <li v-for="(line, index) in features" :key="index">
            {{ line }}
          </li>
        </ul>
      </v-card-text>
      <div class="btn-area">
        <v-btn color="black" :to="localePath(href)" size="large">
          {{ buttonText }}
        </v-btn>
      </div>
    </v-card>
  </div>
</template>

<style lang="scss" scoped>
@import './pricing-card-style.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const props = defineProps({
  color: {
    type: String,
    default: 'primary',
  },
  title: {
    type: String,
    required: true,
  },
  price: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  features: {
    type: Array,
    required: true,
  },
  per: {
    type: String,
    default: '',
  },
  buttonText: {
    type: String,
    required: true,
  },
  href: {
    type: String,
    default: '#',
  },
});

const {
  color, title, price,
  description, features, per,
  buttonText, href,
} = toRefs(props);

const localePath = useLocalePath();
</script>
