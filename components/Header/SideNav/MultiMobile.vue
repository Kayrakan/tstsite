<template>
  <div class="side-menu">
    <v-list class="side-multilv">
      <template
        v-for="(item, index) in dataMenu"
        :key="index"
      >
        <!-- Multilevel Nav -->
        <v-list-group
          v-if="item.child"
          no-action
          class="group-child"
        >
          <template #activator="{props}">
            <v-list-item v-bind="props">
              <v-list-item-title class="menu-list">
                {{ item.name }}
              </v-list-item-title>
            </v-list-item>
          </template>
          <submenu-mobile
            v-for="(subitem, index) in item.child"
            :key="index"
            :menu-items="subitem"
          />
        </v-list-group>
        <!-- Single Nav -->
        <v-list-item
          v-else
          :to="localePath(item.link)"
          :class="{ current: curURL === (curOrigin+langPath+item.link)}"
          link
        >
          <v-list-item-title class="menu-list">
            {{ item.name }}
          </v-list-item-title>
        </v-list-item>
      </template>
      <v-divider />
      <v-list-item
        v-for="(item, index) in ['login', 'register']"
        :key="index"
        :to="localePath('/'+item)"
        :class="{ current: curURL === (curOrigin+langPath+item)}"
        link
      >
        <div>
          <v-list-item-title class="menu-list">
            {{ $t('header_'+item) }}
          </v-list-item-title>
        </div>
      </v-list-item>
    </v-list>
  </div>
</template>

<style scoped lang="scss">
@import '../sidenav-style';
</style>

<script>
import { useLocalePath } from '#imports';
import SubmenuMobile from './SubmenuMobile';

export default {
  components: {
    SubmenuMobile,
  },
  props: {
    dataMenu: {
      type: Array,
      required: true,
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
      isOpen: false,
      curURL: '',
      curOrigin: '',
      langPath: '',
    };
  },
  mounted() {
    this.curURL = window.location.href;
    this.curOrigin = window.location.origin;
    this.langPath = '/' + this.$i18n.locale;
  },
};
</script>
