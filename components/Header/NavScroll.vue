<template>
  <v-navigation-drawer
    v-if="isTablet"
    v-model="openNavMobile"
    fixed
    temporary
    class="mobile-nav"
    location="right"
    width="300"
  >
    <mobile-menu :single-nav="home" :menu="menu" :prefix="prefix" />
  </v-navigation-drawer>
  <v-app-bar
    v-scroll="handleScroll"
    :class="{ fixed: fixed, 'open-side-nav': openNavMobile }"
    class="header"
    fixed
    dense
    app
    height="auto"
  >
    <v-container>
      <div class="header-content">
        <nav class="nav-menu">
          <div class="logo">
            <a href="#home">
              <logo type="landscape" />
            </a>
          </div>
          <div v-if="isDesktop" class="main-menu">
            <header-menu
              :active-menu="activeMenu"
              :menu="menu"
              :prefix="prefix"
              :single-nav="home"
            />
          </div>
          <user-menu />
          <v-btn
            v-if="isTablet"
            :class="{ 'is-active': openNavMobile }"
            class="hamburger hamburger--spin mobile-menu"
            icon
            small
            @click.stop="handleToggleOpen"
          >
            <span class="hamburger-box">
              <span class="bar hamburger-inner" />
            </span>
          </v-btn>
        </nav>
      </div>
    </v-container>
  </v-app-bar>
</template>

<style lang="scss" scoped>
@import './header-style.scss';
</style>

<script>
import Logo from '../Branding/Logo';
import UserMenu from './TopNav/UserMenu';
import SingleNav from './TopNav/SingleNav';
import MobileNav from './SideNav/SingleNavMobile';

export default {
  components: {
    Logo,
    'mobile-menu': MobileNav,
    'header-menu': SingleNav,
    UserMenu,
  },
  props: {
    singleNav: {
      type: Boolean,
      default: false,
    },
    menu: {
      type: Array,
      required: true,
    },
    prefix: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      fixed: false,
      sections: {},
      activeMenu: '',
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
    const section = document.querySelectorAll('.scroll-nav-content > *');
    Array.prototype.forEach.call(section, (e) => {
      this.sections[e.id] = e.offsetTop;
    });
  },
  methods: {
    handleScroll() {
      const scrollPosition = document.documentElement.scrollTop || document.body.scrollTop;
      const topPosition = scrollPosition + 1000;

      Object.keys(this.sections).forEach((i) => {
        if (this.sections[i] <= topPosition) {
          this.activeMenu = i;
        }
      });

      if (scrollPosition > 70) {
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
