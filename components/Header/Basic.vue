<template>
  <v-app-bar
    v-scroll="handleScroll"
    :class="{ fixed: fixed }"
    class="header"
    fixed
    dense
    app
    height="auto"
  >
    <v-container>
      <div class="header-content">
        <nav class="nav-menu">
          <div class="logo start-mobile">
            <nuxt-link :to="localePath(link.home)">
              <logo type="landscape" />
            </nuxt-link>
          </div>
        </nav>
        <nav class="user-menu">
          <v-btn :to="localePath(href)" variant="flat" color="primary">
            {{ $t('header_'+text) }}
          </v-btn>
          <v-spacer
            v-if="isDesktop"
            class="vertical-divider"
          />
          <setting-menu />
        </nav>
      </div>
    </v-container>
  </v-app-bar>
</template>

<style lang="scss" scoped>
@import './header-style.scss';
</style>

<script>
import link from '@/assets/text/link';
import { useLocalePath } from '#imports';
import Logo from '../Branding/Logo';
import Settings from './TopNav/Settings';

export default {
  components: {
    'setting-menu': Settings,
    Logo,
  },
  props: {
    text: {
      type: String,
      default: 'login',
    },
    href: {
      type: String,
      default: link.login,
    },
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
      fixed: false,
      loaded: false,
      openNavMobile: null,
    };
  },
  computed: {
    isTablet() {
      const mdDown = this.$vuetify.display.mdAndDown;
      return mdDown;
    },
    isDesktop() {
      const lgUp = this.$vuetify.display.lgAndUp;
      return lgUp;
    },
  },
  mounted() {
    this.loaded = true;
  },
  methods: {
    handleScroll() {
      if (window.scrollY > 100) {
        this.fixed = true;
      } else {
        this.fixed = false;
      }
    },
    handleToggleOpen() {
      this.openNavMobile = !this.openNavMobile;
    },
  },
};
</script>
