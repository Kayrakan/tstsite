<template>
  <div class="counter-wrap">
    <div class="inner">
      <div class="countdown">
        {{ info && info }}
        <div class="time" :class="{ mini: mini }">
          <vue-countdown
            v-if="counting"
            v-slot="{ days, hours, minutes, seconds }"
            :time="miliseconds"
          >
            <p>
              <span>
                <strong>{{ days }}</strong>
                {{ $t('list_days') }}
              </span>
              <i><strong>:</strong></i>
              <span>
                <strong>{{ hours }}</strong>
                {{ $t('list_hours') }}
              </span>
              <i><strong>:</strong></i>
              <span>
                <strong>{{ minutes }}</strong>
                {{ $t('list_minutes') }}
              </span>
              <i><strong>:</strong></i>
              <span>
                <strong>{{ seconds }}</strong>
                {{ $t('list_seconds') }}
              </span>
            </p>
          </vue-countdown>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './countdown-style.scss';
</style>

<script setup>
import { ref, onMounted, toRefs } from 'vue';

const props = defineProps({
  miliseconds: {
    type: Number,
    required: true,
  },
  info: {
    type: String,
    default: null,
  },
  mini: {
    type: Boolean,
    default: false,
  },
});

const { miliseconds, info, mini } = toRefs(props);

const counting = ref(false);

onMounted(() => {
  counting.value = true;
});
</script>
