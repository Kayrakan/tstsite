<template>
  <div>
    <nuxt-layout name="auth" :link="link.register" text-link="register">
      <login-form />
    </nuxt-layout>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script setup>
import brand from '@/assets/text/brand';
import LoginForm from '@/components/Forms/Login';
import link from '@/assets/text/link';
import { useHead } from '#app';
import { definePageMeta } from '#imports';

useHead({
  title: brand.name + ' - Login',
});

definePageMeta({
  layout: false,
});
</script>
