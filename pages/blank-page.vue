<template>
  <div>
    <div class="container-general">
      <div class="space-top space-bottom">
        <h2 class="display-3 text-center mb-4">
          {{ $t('title') }}
        </h2>
        <h4 class="display-1 text-center">
          {{ $t('subtitle') }}
        </h4>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '@/assets/scss/pages';
</style>

<script>
import brand from '@/assets/text/brand';

export default {
  head() {
    return {
      title: 'Blank Page | ' + brand.desc,
    };
  },
};
</script>
