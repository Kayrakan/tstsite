<template>
  <v-container class="shortcut">
    <v-row class="scroll-tablet" :class="{ spacing4: isDesktop }">
      <v-col sm="4" cols="10">
        <div class="shortcut-btn primary">
          <nuxt-link v-ripple :to="localePath(link.blog)">
            <div class="icon3d">
              <icons3d icon="mdi-newspaper-variant" color="primary-double" />
            </div>
            <strong :class="isDesktop ? 'use-text-subtitle' : 'use-text-subtitle2'">
              {{ $t('faq_help3') }}
            </strong>
            <p class="use-text-paragraph">
              {{ $t('list_title') }}
            </p>
          </nuxt-link>
        </div>
      </v-col>
      <v-col sm="4" cols="10">
        <div class="shortcut-btn secondary">
          <nuxt-link v-ripple :to="localePath(link.contact)">
            <div class="icon3d">
              <icons3d icon="mdi-code-greater-than-or-equal" color="secondary-double" />
            </div>
            <strong :class="isDesktop ? 'use-text-subtitle' : 'use-text-subtitle2'">
              {{ $t('faq_help1') }}
            </strong>
            <p class="use-text-paragraph">
              {{ $t('faq_title') }}
            </p>
          </nuxt-link>
        </div>
      </v-col>
      <v-col sm="4" cols="10">
        <div class="shortcut-btn accent">
          <nuxt-link v-ripple :to="localePath(link.contact)">
            <div class="icon3d">
              <icons3d icon="mdi-card-account-details" color="accent-double" />
            </div>
            <strong :class="isDesktop ? 'use-text-subtitle' : 'use-text-subtitle2'">
              {{ $t('btn_contact') }}
            </strong>
            <p class="use-text-paragraph">
              {{ $t('faq_luck') }}
            </p>
          </nuxt-link>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
@import './faq-style.scss';
</style>

<script setup>
import { useDisplay } from 'vuetify';
import { useLocalePath } from '#imports';
import link from '@/assets/text/link';
import Icons3d from '../../Icons3d';

const { mdAndUp: isDesktop } = useDisplay();
const localePath = useLocalePath();
</script>
