<template>
  <nav class="user-menu">
    <v-btn
      v-if="isDesktop"
      :to="localePath(link.login)"
      variant="text"
    >
      {{ $t('login') }}
    </v-btn>
    <v-btn
      v-if="isDesktop"
      :to="localePath(link.register)"
      color="primary"
      variant="flat"
    >
      {{ $t('register') }}
    </v-btn>
    <v-spacer
      v-if="isDesktop"
      class="vertical-divider"
    />
    <setting-menu v-if="loaded" />
  </nav>
</template>

<style lang="scss" scoped>
@import '../header-style.scss';
</style>

<script>
import link from '@/assets/text/link';
import { useLocalePath } from '#imports';
import Settings from './Settings';

export default {
  components: {
    'setting-menu': Settings,
  },
  setup() {
    const localePath = useLocalePath();
    return {
      localePath,
    };
  },
  data() {
    return {
      link,
      loaded: false,
    };
  },
  computed: {
    isDesktop() {
      const smUp = this.$vuetify.display.smAndUp;
      return smUp;
    },
  },
  mounted() {
    this.loaded = true;
  },
};
</script>
