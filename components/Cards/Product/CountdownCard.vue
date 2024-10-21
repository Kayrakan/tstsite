<template>
  <v-card class="product-card portrait over">
    <nuxt-link v-ripple draggable="false" focus-ripple :to="localePath(href)" class="hidden-link">
      &nbsp;
    </nuxt-link>
    <div class="head">
      <div>
        <v-avatar
          v-for="(item, index) in avatars"
          :key="index.toString()"
          class="avatar"
          alt="avatar"
          :image="item || defaultUser"
        />
      </div>
      <v-chip class="price">
        {{ bid }}+ Place Bid
      </v-chip>
    </div>
    <figure>
      <v-img
        :src="img"
        height="200px"
        cover
      />
      <span class="countdown">
        <span class="time">
          <vue-countdown
            v-if="counting"
            v-slot="{ days, hours, minutes, seconds }"
            :time="timeleft"
            @end="onCountdownEnd"
          >
            <span>
              <span>
                <strong>{{ days }}</strong>
                Days
              </span>
              <i><strong>:</strong></i>
              <span>
                <strong>{{ hours }}</strong>
                Hours
              </span>
              <i><strong>:</strong></i>
              <span>
                <strong>{{ minutes }}</strong>
                Minutes
              </span>
              <i><strong>:</strong></i>
              <span>
                <strong>{{ seconds }}</strong>
                Seconds
              </span>
            </span>
          </vue-countdown>
          <strong v-else>Expired</strong>
        </span>
      </span>
    </figure>
    <div class="desc">
      <v-card-text class="text">
        <h2 class="title pb-2 text-truncate">
          {{ title }}
        </h2>
        <p class="use-text-paragraph">
          circulation:
          &nbsp;
          {{ desc }}
        </p>
      </v-card-text>
      <div>
        <v-card-actions class="property">
          <strong v-if="price > 0">
            {{ price }}
            ETH
          </strong>
          <div v-if="like > 0" class="like">
            <i class="ion-ios-heart-outline" />
            {{ like }}
          </div>
        </v-card-actions>
      </div>
    </div>
  </v-card>
</template>

<style lang="scss" scoped>
@import './countdown-card.scss';
</style>

<script setup>
import { ref, onMounted, toRefs } from 'vue';
import { useLocalePath } from '#imports';
import defaultUser from '@/assets/images/avatars/pp_boy4.svg';

const props = defineProps({
  img: {
    type: String,
    required: true,
  },
  title: {
    type: String,
    required: true,
  },
  desc: {
    type: String,
    required: true,
  },
  like: {
    type: Number,
    default: 0,
  },
  bid: {
    type: Number,
    required: true,
  },
  price: {
    type: Number,
    default: 0,
  },
  avatars: {
    type: Array,
    required: true,
  },
  href: {
    type: String,
    default: '#',
  },
  timeleft: {
    type: Number,
    default: 0,
  },
});

const {
  img, title, desc,
  like, bid, price,
  href, avatars, timeleft,
} = toRefs(props);

const counting = ref(false);
const localePath = useLocalePath();

onMounted(() => {
  counting.value = true;
});

function onCountdownEnd() {
  counting.value = false;
}
</script>
