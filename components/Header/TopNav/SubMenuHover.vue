<template>
  <div class="parent-hover" v-if="menuItems.child">
    <v-list-item link>
      <v-list-item-title
        v-text="menuItems.name"
        class="menu-list"
      />
      <template v-slot:append>
        <v-icon color="grey lighten-1" class="arrow-icon">mdi-chevron-right</v-icon>
      </template>
    </v-list-item>
    <v-list class="submenu-hover">
      <!-- SubMenu -->
      <v-card elevation="4">
        <submenu
          v-for="(subitem, index) in menuItems.child"
          :key="index"
          :menu-items="subitem"
        />
      </v-card>
    </v-list>
  </div>
  <v-list-item
    v-else 
    :to="menuItems.link ? localePath(menuItems.link) : '#'"
    :class="{ current: curURL === (curOrigin+langPath+menuItems.link)}"
    @click="handleClose()"
  >
    <v-list-item-title
      class="menu-list"
      v-text="$t('header_'+menuItems.name)"
    />
  </v-list-item>
</template>

<style lang="scss" scoped>
@import '../header-style.scss';
</style>

<script>
import { useLocalePath } from '#imports';

export default {
  name: 'Submenu',
  setup() {
    const localePath = useLocalePath();
    return {
      localePath
    };
  },
  data() {
    return {
      showMenu: false,
      curURL: '',
      curOrigin: '',
      langPath: ''
    }
  },
  mounted() {
    this.curURL = window.location.href
    this.curOrigin = window.location.origin
    this.langPath = '/' + this.$i18n.locale
  },
  props: {
    menuItems: {
      type: Object,
      required: true
    }
  },
  methods: {
    handleClose() {
      this.showMenu = false
    }
  }
}
</script>
