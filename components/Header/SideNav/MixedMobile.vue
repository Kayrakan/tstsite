<template>
  <div class="side-menu">
    <v-list dense>
      <template v-if="singleNav">
        <v-list-item
          v-for="(item, index) in menuPrimary"
          :key="index"
          :href="'#'+item.id"
          :class="{ current: curURL === (curOrigin+langPath+item.id)}"
          link
        >
          <div>
            <v-list-item-title class="menu-list">
              {{ $t(prefix+'.header_'+item.name) }}
            </v-list-item-title>
          </div>
        </v-list-item>
      </template>
      <template v-else>
        <v-list-item
          v-for="(item, index2) in menuPrimary"
          :key="index2"
          :to="{ path: localePath('/'), hash: '#'+item.id }"
          :class="{ current: curURL === (curOrigin+langPath+item.id)}"
          link
        >
          <div>
            <v-list-item-title class="menu-list">
              {{ $t(prefix+'.header_'+item.name) }}
            </v-list-item-title>
          </div>
        </v-list-item>
      </template>
      <v-list-group class="group-child">
        <template #activator="{props}">
          <v-list-item v-bind="props">
            <v-list-item-title class="menu-list">
              {{ $t('header_sample_page') }}
            </v-list-item-title>
          </v-list-item>
        </template>
        <v-list
          v-for="(subitem, index) in menuSecondary"
          :key="index"
        >
          <v-list-subheader class="title-mega">
            {{ $t('header_'+subitem.name) }}
          </v-list-subheader>
          <div>
            <v-list-item
              v-for="(item, index) in subitem.child"
              :key="index"
              :to="localePath(item.link)"
              :class="{ current: curURL === (curOrigin+langPath+item.link)}"
            >
              <div>
                <v-list-item-title class="menu-list" v-text="$t('header_'+item.name)" />
              </div>
            </v-list-item>
          </div>
        </v-list>
      </v-list-group>
    </v-list>
    <v-divider class="my-5" />
    <v-list dense>
      <v-list-item
        v-for="(item, index) in ['login', 'register']"
        :key="index"
        :to="localePath('/' + item)"
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

export default {
  props: {
    menuPrimary: {
      type: Array,
      required: true,
    },
    menuSecondary: {
      type: Array,
      required: true,
    },
    prefix: {
      type: String,
      required: true,
    },
    singleNav: {
      type: Boolean,
      default: false,
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
