<template>
  <v-dialog
    v-model="dialog"
    max-width="690"
  >
    <v-card class="video-popup">
      <v-card-title class="headline d-flex justify-space-between">
        <h4 class="use-text-subtitle2">
          {{ $t('fintech.feature_title3') }}
        </h4>
        <v-btn class="close-btn" variant="text" icon @click="handleVideoClose()">
          <v-icon>mdi-close</v-icon>
        </v-btn>
      </v-card-title>
      <div v-if="yt.use" class="text-center mb-3">
        <YouTube
          ref="youtubePopup"
          :src="videoIdPopup"
          :vars="playerVarsPopup"
          :width="640"
          :height="360"
          class="youtube"
          @ready="onReadyPopup"
        />
      </div>
    </v-card>
  </v-dialog>
  <div class="banner-wrap">
    <div class="carousel">
      <splide
        ref="sliderBanner"
        class="slider"
        :options="slickOptions"
        @splide:active="handleAfterChange"
      >
        <splide-slide>
          <div id="slide1" class="slide">
            <div class="inner">
              <div class="img background-banner">
                <div class="deco-mask">
                  <svg class="main">
                    <use xlink:href="/images/decoration/banner-mask.svg#main" />
                  </svg>
                  <svg class="darken">
                    <use xlink:href="/images/decoration/banner-mask.svg#main" />
                  </svg>
                </div>
                <div class="deco-line">
                  <svg class="primary">
                    <use xlink:href="/images/decoration/banner-line.svg#main" />
                  </svg>
                  <svg class="secondary">
                    <use xlink:href="/images/decoration/banner-line.svg#main" />
                  </svg>
                </div>
                <img v-if="!play || !isDesktop" class="cover" :src="imgAPI.photosL[49]" alt="cover">
                <div v-if="yt.use && isDesktop" class="video">
                  <YouTube
                    ref="youtubeBg"
                    :src="videoIdBg"
                    :vars="playerVarsBg"
                    :width="1080"
                    :height="720"
                    @ready="playing"
                    @state-change="ended"
                  />
                </div>
              </div>
              <v-container>
                <v-row class="spacing6">
                  <v-col class="pe-sm-15 pe-sm-10 px-6" md="7" cols="12">
                    <div class="text">
                      <h4 :class="isTablet ? 'use-text-title2' : 'use-text-title'">
                        {{ $t('fintech.banner_title') }}
                        <span class="text-uppercase" :class="currentTheme === 'dark' ? 'use-text-grd-triple-light' : 'use-text-grd-triple-main'">
                          {{ $t('fintech.banner_highlight') }}
                        </span>
                      </h4>
                      <h5 :class="isTablet ? 'use-text-subtitle2' : 'use-text-subtitle'">
                        {{ $t('fintech.banner_desc') }}
                      </h5>
                      <div class="btn-area download">
                        <a href="#">
                          <img src="/images/wallet/app-store.png" alt="app store">
                        </a>
                        <a href="#">
                          <img src="/images/wallet/play-store.png" alt="play store">
                        </a>
                      </div>
                    </div>
                  </v-col>
                  <v-col md="5" cols="12">
                    <div class="deco-banner">
                      <div class="mobile-art">
                        <mobile-app
                          :screen="imgAPI.apps[14]"
                          :top="imgAPI.apps[8]"
                          :left="imgAPI.apps[10]"
                          :right="imgAPI.apps[9]"
                        />
                      </div>
                    </div>
                  </v-col>
                </v-row>
              </v-container>
            </div>
          </div>
        </splide-slide>
        <splide-slide>
          <div id="slide2" class="slide">
            <div class="inner">
              <v-container>
                <v-row justify="end" align="center" :class="[isMobile ? 'column-reverse' : 'row']">
                  <v-col md="6" cols="12">
                    <div class="deco-banner">
                      <div class="sharing-art">
                        <sharing-art
                          :person-big="imgAPI.avatar[12]"
                          :person-medium="imgAPI.avatar[11]"
                          :person-small1="imgAPI.avatar[20]"
                          :person-small2="imgAPI.avatar[21]"
                        />
                      </div>
                    </div>
                  </v-col>
                  <v-col md="6" cols="12">
                    <div class="text">
                      <h4 :class="isTablet ? 'use-text-title2' : 'use-text-title'">
                        {{ $t('fintech.banner_title') }}
                        <span class="text-uppercase" :class="currentTheme === 'dark' ? 'use-text-grd-triple-light' : 'use-text-grd-triple-main'">
                          {{ $t('fintech.banner_highlight') }}
                        </span>
                      </h4>
                      <h5 :class="isTablet ? 'use-text-subtitle2' : 'use-text-subtitle'">
                        {{ $t('fintech.banner_desc') }}
                      </h5>
                      <div class="btn-area">
                        <v-btn
                          size="large"
                          color="primary"
                          class="button"
                          :to="localePath(link.register)"
                        >
                          {{ $t('btn_get') }}
                        </v-btn>
                        <v-btn
                          size="large"
                          color="secondary"
                          class="button"
                          variant="outlined"
                          href="#"
                        >
                          {{ $t('btn_detail') }}
                        </v-btn>
                      </div>
                    </div>
                  </v-col>
                </v-row>
              </v-container>
            </div>
          </div>
        </splide-slide>
        <splide-slide>
          <div id="slide3" class="slide center-content">
            <div class="inner">
              <v-container>
                <v-row justify="center">
                  <v-col sm="12" cols="12" class="pt-15 mt-5 pa-0">
                    <div class="text text-center">
                      <h4 :class="isTablet ? 'use-text-title2' : 'use-text-title'">
                        {{ $t('fintech.banner_title') }}
                        <span class="text-uppercase" :class="currentTheme === 'dark' ? 'use-text-grd-triple-light' : 'use-text-grd-triple-main'">
                          {{ $t('fintech.banner_highlight') }}
                        </span>
                      </h4>
                      <h5 :class="isTablet ? 'use-text-subtitle2' : 'use-text-subtitle'">
                        {{ $t('fintech.banner_desc') }}
                      </h5>
                    </div>
                  </v-col>
                  <v-col cols="12">
                    <div class="img h-banner">
                      <div class="img background-banner">
                        <div class="deco-mask">
                          <svg class="main">
                            <use xlink:href="/images/decoration/banner-mask.svg#main" />
                          </svg>
                          <svg class="darken">
                            <use xlink:href="/images/decoration/banner-mask.svg#main" />
                          </svg>
                        </div>
                        <img class="cover" :src="imgAPI.photosL[49]" alt="cover">
                      </div>
                      <div class="deco-banner">
                        <div class="video-art">
                          <video-banner
                            :action="handleVideoOpen"
                            :cover="imgAPI.photosL[48]"
                            :top-left="imgAPI.apps[4]"
                            :top-right="imgAPI.apps[5]"
                            :bottom-left="imgAPI.apps[7]"
                            :bottom-right="imgAPI.apps[6]"
                          />
                          <div v-if="isMobileXs" class="additional-art">
                            <video-banner
                              :cover="imgAPI.apps[16]"
                              :top-left="imgAPI.apps[5]"
                              :top-right="imgAPI.apps[1]"
                              :bottom-left="imgAPI.apps[2]"
                              :bottom-right="imgAPI.apps[16]"
                            />
                          </div>
                        </div>
                      </div>
                    </div>
                  </v-col>
                </v-row>
              </v-container>
            </div>
          </div>
        </splide-slide>
      </splide>
    </div>
    <div class="slide-nav-group">
      <hidden point="smDown">
        <v-container>
          <nav class="slide-nav">
            <v-btn
              :class="{ active: currentSlide === 0 }"
              variant="text"
              @click="gotoSlide(0)"
            >
              <strong>First Slide</strong>
              Interdum et malesuada fames ac ante
            </v-btn>
            <v-divider class="divider" vertical inset />
            <v-btn
              :class="{ active: currentSlide === 1 }"
              variant="text"
              @click="gotoSlide(1)"
            >
              <strong>Second Slide</strong>
              Interdum et malesuada fames ac ante
            </v-btn>
            <v-divider class="divider" vertical inset />
            <v-btn
              :class="{ active: currentSlide === 2 }"
              variant="text"
              @click="gotoSlide(2)"
            >
              <strong>Third Slide</strong>
              Interdum et malesuada fames ac ante
            </v-btn>
          </nav>
        </v-container>
      </hidden>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import './banner-style';
</style>

<script setup>
import { ref, onMounted } from 'vue';
import { useDisplay, useRtl, useTheme } from 'vuetify';
import { Splide, SplideSlide } from '@splidejs/vue-splide';
import yt from '@/config/youtube';
import link from '@/assets/text/link';
import imgAPI from '@/assets/images/imgAPI';
import { useLocalePath } from '#imports';
import MobileApp from '../../Artworks/MobileApp';
import SharingArt from '../../Artworks/Sharing';
import VideoBanner from '../../Artworks/VideoBanner';
import Hidden from '../../Utils/Hidden';

const localePath = useLocalePath();
const currentSlide = ref(0);
const sliderBanner = ref(null);
const slickOptions = ref({
  pagination: false,
  arrows: false,
  perPage: 1,
  type: 'loop',
  speed: 1000,
  easing: 'ease',
  direction: 'ltr',
  reducedMotion: {
    speed: 1000,
    rewindSpeed: 1000,
  },
  breakpoints: {
    800: {
      pagination: true,
    },
  },
});

// Video Popup Settings
const dialog = ref(false);
const videoIdPopup = '9vPfeczePww';
const youtubePopup = ref(null);
const playerVarsPopup = {
  autoplay: 0,
  controls: 1,
  rel: 0,
  showinfo: 1,
  mute: 0,
  origin: 'https://localhost:8000',
};

// Video Background
const youtubeBg = ref(null);
const play = ref(false);
const videoIdBg = '0cdLuY6R_kI';
const playerVarsBg = {
  autoplay: 1,
  controls: 0,
  rel: 0,
  showinfo: 0,
  mute: 1,
  origin: 'http://localhost:8000',
};

const { xs: isMobileXs } = useDisplay();
const { smAndDown: isMobile } = useDisplay();
const { md: isTablet } = useDisplay();
const { mdAndUp: isDesktop } = useDisplay();

const { name: currentTheme } = useTheme();
const { isRtl } = useRtl();

onMounted(() => {
  setTimeout(() => {
    if (isRtl.value) {
      slickOptions.value.direction = 'rtl';
    } else {
      slickOptions.value.direction = 'ltr';
    }
  }, 100);
});

// Video Popup Function
function handleVideoOpen() {
  if (yt.use) {
    dialog.value = true;
  }
}

function onReadyPopup() {
  youtubePopup.value.playVideo();
}

function handleVideoClose() {
  dialog.value = false;
  youtubePopup.value.pauseVideo();
}

// Video Background Function
function playing() {
  play.value = true;
}

function ended(val) {
  if (val.data === 0) {
    youtubeBg.value.playVideo();
  }
}

// Slider banner Function
function handleAfterChange(slide) {
  currentSlide.value = slide.index;
}

function gotoSlide(index) {
  sliderBanner.value.go(index);
}
</script>
