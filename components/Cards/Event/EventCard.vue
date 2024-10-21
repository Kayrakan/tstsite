<template>
  <v-card class="event-card" :class="color">
    <v-card-item>
      <h3 class="date">
        {{ date }}
      </h3>
      <h5 class="location">
        {{ location }}
      </h5>
      <p>{{ desc }}</p>
      <div class="btn-area">
        <v-btn v-if="actionPrimary !== ''" color="black" :to="localePath(actionPrimary.href)">
          {{ actionPrimary.text }}
        </v-btn>
        <v-btn v-if="actionSecondary !== ''" color="black" :to="localePath(actionSecondary.href)" variant="outlined">
          {{ actionSecondary.text }}
        </v-btn>
      </div>
    </v-card-item>
  </v-card>
</template>

<style scoped lang="scss">
@import './event-card.scss';
</style>

<script setup>
import { toRefs } from 'vue';
import { useLocalePath } from '#imports';

const props = defineProps({
  color: {
    type: String,
    default: 'primary',
  },
  date: {
    type: String,
    required: true,
  },
  location: {
    type: String,
    required: true,
  },
  desc: {
    type: String,
    required: true,
  },
  actionPrimary: {
    type: Object,
    default: null,
  },
  actionSecondary: {
    type: Object,
    default: null,
  },
});

const {
  color, date, location,
  desc, actionPrimary, actionSecondary,
} = toRefs(props);

const localePath = useLocalePath();

</script>
