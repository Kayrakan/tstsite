<template>
  <div class="root">
    <v-container :class="[isMobile ? 'max-sm' : 'max-lg']">
      <v-row>
        <v-col lg="1" cols="12" class="pa-0" />
        <v-col lg="11" cols="12" class="pa-0">
          <div class="about">
            <div class="reward">
              <div class="item">
                <figure>
                  <img src="/images/profile/reward1.svg" alt="badge">
                </figure>
                <p class="use-text-paragraph">
                  Special Mention
                </p>
                <h5 :class="isTablet ? 'use-text-paragraph' : 'use-text-subtitle'">
                  Awards
                </h5>
              </div>
              <div class="item">
                <figure>
                  <img src="/images/profile/reward2.svg" alt="badge">
                </figure>
                <p class="use-text-paragraph">
                  100k videos
                </p>
                <h5 :class="isTablet ? 'use-text-paragraph' : 'use-text-subtitle'">
                  Subscriber
                </h5>
              </div>
              <div class="item">
                <figure>
                  <img src="/images/profile/reward3.svg" alt="badge">
                </figure>
                <p class="use-text-paragraph">
                  Best Filmography
                </p>
                <h5 :class="isTablet ? 'use-text-paragraph' : 'use-text-subtitle'">
                  Footage
                </h5>
              </div>
            </div>
            <hidden point="mdUp">
              <div class="mt-10">
                <h6 class="use-text-subtitle2">
                  {{ $t('profile.banner_desc') }}
                </h6>
                <div class="socmed">
                  <v-btn icon small variant="text" class="margin">
                    <i class="ion-logo-facebook" />
                  </v-btn>
                  <v-btn icon small variant="text" class="margin">
                    <i class="ion-logo-twitter " />
                  </v-btn>
                  <v-btn icon small variant="text" class="margin">
                    <i class="ion-logo-instagram" />
                  </v-btn>
                  <v-btn icon small variant="text" class="margin">
                    <i class="ion-logo-linkedin" />
                  </v-btn>
                </div>
              </div>
            </hidden>
            <div class="photo">
              <figure class="avatar">
                <img :src="imgAPI.profile[3]" alt="avatar">
              </figure>
              <v-card class="hire-paper">
                <div class="hire">
                  <strong>
                    <span class="online" />
                    {{ $t('profile.banner_available') }}
                  </strong>
                </div>
                <v-btn
                  class="btn"
                  block
                  size="large"
                  href="#contact"
                  color="secondary"
                  @click="scrollToContact"
                >
                  {{ $t('profile.banner_contact') }}
                </v-btn>
              </v-card>
            </div>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
@import './profile-style.scss';
</style>

<script setup>
import { inject, ref, onMounted } from 'vue';
import { useDisplay } from 'vuetify';
import imgAPI from '@/assets/images/imgAPI';
import Hidden from '../../Utils/Hidden';

const { smAndDown: isMobile } = useDisplay();
const { lgAndDown: isTablet } = useDisplay();

const smoothScroll = inject('smoothScroll');
const myEl = ref(null);

onMounted(() => {
  myEl.value = document.getElementById('contact');
});

function scrollToContact() {
  smoothScroll({
    scrollTo: myEl.value,
    hash: '#contact',
    offset: -300,
    updateHistory: true,
  });
}
</script>
