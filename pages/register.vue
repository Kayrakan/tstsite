<template>
  <div>
    <nuxt-layout name="auth" :link="link.login" text-link="login">
      <register-form />
    </nuxt-layout>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import brand from '@/assets/text/brand';
import RegisterForm from '@/components/Forms/Register';
import link from '@/assets/text/link';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Register',
});

definePageMeta({
  layout: false,
});
</script>
