<template>
  <vue-easy-lightbox
    v-if="loaded"
    :visible="visible"
    :imgs="imgs"
    :index="index"
    @hide="handleHide"
  />
  <div class="root">
    <v-container>
      <title-main :text="$t('profile.gallery_title')" align="center" />
      <v-container class="tab">
        <div class="filter">
          <v-btn
            :class="{ selected: filter === 'all' }"
            variant="text"
            @click="filterChildren('all')"
          >
            All
          </v-btn>
          <v-btn
            :class="{ selected: filter === 'cat1' }"
            variant="text"
            @click="filterChildren('cat1')"
          >
            Category 1
          </v-btn>
          <v-btn
            :class="{ selected: filter === 'cat2' }"
            variant="text"
            @click="filterChildren('cat2')"
          >
            Category 2
          </v-btn>
          <v-btn
            :class="{ selected: filter === 'cat3' }"
            variant="text"
            @click="filterChildren('cat3')"
          >
            Category 3
          </v-btn>
          <v-btn
            :class="{ selected: filter === 'cat4' }"
            variant="text"
            @click="filterChildren('cat4')"
          >
            Category 4
          </v-btn>
          <v-btn
            :class="{ selected: filter === 'cat5' }"
            variant="text"
            @click="filterChildren('cat5')"
          >
            Category 5
          </v-btn>
        </div>
      </v-container>
      <hidden point="xsDown">
        <div class="massonry">
          <div>
            <div
              v-for="(item, index) in data"
              :key="index"
              class="item"
            >
              <div
                data-aos="fade-up"
                data-aos-offset="200"
                :data-aos-delay="200 + (100 * index)"
                data-aos-duration="300"
              >
                <photo-card
                  :img="item.img"
                  :title="item.title"
                  :link="item.link"
                  :size="item.size"
                  :show-img="() => showImg(index)"
                />
              </div>
            </div>
          </div>
        </div>
        <p v-if="data.length < 1" class="overline text-center">
          {{ $t('util_soon') }}
        </p>
      </hidden>
      <hidden point="smUp">
        <p v-if="data.length < 1" class="overline text-center">
          {{ $t('util_soon') }}
        </p>
        <splide ref="slick" :options="slickOptions">
          <splide-slide
            v-for="(item, index) in data"
            :key="index"
          >
            <div class="item-carousel">
              <photo-card
                :img="item.img"
                :title="item.title"
                :link="item.link"
                :size="item.size"
                :show-img="() => showImg(index)"
              />
            </div>
          </splide-slide>
        </splide>
      </hidden>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './portfolios-style.scss';
</style>

<script setup>
import { ref, computed, onMounted } from 'vue';
import { useDisplay, useRtl } from 'vuetify';
import AOS from 'aos';
import { Splide, SplideSlide } from '@splidejs/vue-splide';
import imgAPI from '@/assets/images/imgAPI';
import PhotoCard from '../../Cards/Media/PhotoCard';
import TitleMain from '../../Title';
import Hidden from '../../Utils/Hidden';

const portfolio = [
  {
    img: imgAPI.photosL[4],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'short',
    category: 'cat1',
  },
  {
    img: imgAPI.photosL[41],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'long',
    category: 'cat2',
  },
  {
    img: imgAPI.photosL[34],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'short',
    category: 'cat3',
  },
  {
    img: imgAPI.photosP[11],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'long',
    category: 'cat1',
  },
  {
    img: imgAPI.photosS[2],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'short',
    category: 'cat2',
  },
  {
    img: imgAPI.photosL[5],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'short',
    category: 'cat3',
  },
  {
    img: imgAPI.photosL[32],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'short',
    category: 'cat1',
  },
  {
    img: imgAPI.photosL[2],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'short',
    category: 'cat2',
  },
  {
    img: imgAPI.photosP[21],
    title: 'Aenean facilisis vitae purus',
    link: 'linkofthisitem.com',
    size: 'long',
    category: 'cat2',
  },
];

const visible = ref(false);
const index = ref(0);
const data = ref([]);
const loaded = ref(false);
const filter = ref('all');
const slickOptions = ref({
  pagination: false,
  speed: 500,
  perPage: 1,
  arrows: false,
  direction: 'ltr',
});

const { mdAndUp: isDesktop } = useDisplay();
const { isRtl } = useRtl();

const imgs = computed(() => {
  const arr = [];
  data.value.map(item => {
    arr.push(item.img);
    return arr;
  });
  return arr;
});

onMounted(() => {
  data.value = portfolio;
  loaded.value = true;
  AOS.init({
    once: true,
  });

  setTimeout(() => {
    if (isRtl.value) {
      slickOptions.value.direction = 'rtl';
    } else {
      slickOptions.value.direction = 'ltr';
    }
  }, 100);
});

function showImg(idx) {
  index.value = idx;
  visible.value = true;
}

function handleHide() {
  visible.value = false;
}

function filterChildren(name) {
  if (isDesktop) {
    data.value = [];
  }

  setTimeout(() => {
    if (name !== 'all') {
      const filteredData = portfolio.filter(item => item.category === name);
      data.value = filteredData;
      filter.value = name;
    } else {
      data.value = portfolio;
      filter.value = 'all';
    }
  }, 100);
}
</script>
