<template>
  <parallax-left />
  <div class="root">
    <v-container>
      <v-row :justify="isDesktop ? 'start' : 'center'" :class="{ 'spacing6' : isDesktop }">
        <v-col md="5" cols="12">
          <title-main :text="$t('wallet.chart_title')" />
          <p class="use-text-subtitle2">
            {{ $t('wallet.chart_desc') }}
          </p>
          <div class="py-10">
            <v-btn
              class="btn"
              :to="localePath(link.register)"
              color="primary"
            >
              {{ $t('btn_get') }}
            </v-btn>
          </div>
        </v-col>
        <v-col md="7" cols="12">
          <ul class="chart-wrap">
            <li v-for="(item, index) in coinData" :key="index">
              <div class="coin">
                <v-avatar class="logo">
                  <img :src="item.logo" :alt="item.name">
                </v-avatar>
                <h5>
                  {{ item.name }}
                </h5>
              </div>
              <div class="price">
                <h6>$ {{ item.price }}</h6>
                <div v-if="item.status === 'down'" class="down">
                  <i>▼</i>{{ item.percent }}%
                </div>
                <div v-if="item.status === 'up'" class="up">
                  <i>▲</i>{{ item.percent }}%
                </div>
                <div v-if="item.status === 'stay'" class="stay">
                  <i>-</i>{{ item.percent }}%
                </div>
              </div>
              <div v-if="loaded" class="progress">
                <line-chart
                  :chart-id="'chart'+index"
                  :height="60"
                  :options="chartOpt"
                  :chart-data="item.dataCollection"
                  :labels="dataLabels"
                  :type="item.status"
                />
              </div>
            </li>
          </ul>
          <div class="px-6">
            <v-btn class="btn" variant="text" :to="localePath(link.register)" size="large" color="secondary">
              {{ $t('btn_get') }}
              <v-icon class="ms-1">
                mdi-arrow-right
              </v-icon>
            </v-btn>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './chart-price-style.scss';
</style>

<script setup>
import { onMounted, ref } from 'vue';
import { useDisplay } from 'vuetify';
import imgAPI from '@/assets/images/imgAPI';
import link from '@/assets/text/link';
import { useLocalePath } from '#imports';
import LineChart from './LineChart';
import ParallaxLeft from '../Parallax/ParallaxLeft';
import TitleMain from '../../Title';

const coinData = [
  {
    name: 'BTC',
    logo: imgAPI.logos[48],
    status: 'up',
    price: 1234,
    percent: 3,
    dataCollection: [11, 13, 10, 4, 10, 12, 13, 16, 17, 20, 16, 16, 13, 10, 4, 6, 8, 9, 13, 16, 17, 20, 14, 16],
  },
  {
    name: 'DASH',
    logo: imgAPI.logos[52],
    status: 'up',
    price: 1234,
    percent: 2,
    dataCollection: [13, 16, 17, 20, 16, 16, 13, 10, 11, 29, 10, 4, 10, 12, 4, 17, 20, 16, 6, 8, 9, 13, 16, 17],
  },
  {
    name: 'NAN',
    logo: imgAPI.logos[56],
    status: 'down',
    price: 1234,
    percent: 10,
    dataCollection: [10, 12, 13, 16, 17, 20, 16, 16, 13, 11, 8, 10, 4, 10, 4, 6, 8, 9, 13, 16, 17, 20, 16, 6],
  },
  {
    name: 'MNR',
    logo: imgAPI.logos[55],
    status: 'up',
    price: 1234,
    percent: 6,
    dataCollection: [11, 10, 10, 16, 16, 13, 10, 4, 6, 8, 9, 13, 16, 17, 20, 16, 16, 4, 10, 12, 13, 16, 17, 20],
  },
  {
    name: 'IOT',
    logo: imgAPI.logos[53],
    status: 'down',
    price: 1234,
    percent: 3,
    dataCollection: [11, 9, 10, 4, 10, 12, 13, 16, 17, 20, 16, 16, 13, 10, 4, 6, 8, 9, 13, 16, 17, 20, 16, 16],
  },
];

const localePath = useLocalePath();
const { smAndUp: isDesktop } = useDisplay();
const loaded = ref(false);

onMounted(() => {
  loaded.value = true;
});

const chartOpt = {
  gradientBackground: true,
  plugins: {
    title: {
      display: true,
      text: 'Chart.js Line Chart',
    },
  },
  interaction: {
    mode: 'index',
    intersect: false,
  },
  responsive: true,
  maintainAspectRatio: false,
  legend: {
    display: false,
  },
  elements: {
    line: {
      tension: 0,
    },
    point: {
      radius: 1,
    },
  },
  scales: {
    x: {
      border: {
        display: false,
      },
      grid: {
        display: false,
      },
      ticks: {
        display: false,
      },
    },
    y: {
      border: {
        display: false,
      },
      grid: {
        display: false,
      },
      ticks: {
        display: false,
      },
    },
  },
};

const dataLabels = ['1PM', '2PM', '3PM', '4PM', '5PM', '6PM', '7PM', '8PM', '9PM', '10PM', '11PM', '00AM', '1AM', '2AM', '3AM', '4AM', '5AM', '6AM', '7AM', '8AM', '9AM', '10AM', '11AM', '12PM']; // eslint-disable-line
</script>
