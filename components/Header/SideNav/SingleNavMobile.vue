<template>
  <v-list dense>
    <template v-if="singleNav">
      <v-list-item
        v-for="(item, index) in menu"
        :key="index"
        :href="'#'+item.id"
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
        v-for="(item, index2) in menu"
        :key="index2"
        :to="{ path: localePath('/'), hash: '#'+item.id }"
        link
      >
        <div>
          <v-list-item-title class="menu-list">
            {{ $t(prefix+'.header_'+item.name) }}
          </v-list-item-title>
        </div>
      </v-list-item>
    </template>
  </v-list>
  <v-divider />
  <v-list dense>
    <v-list-item
      v-for="(item, index) in ['login', 'register']"
      :key="index"
      :to="localePath('/' + item)"
      link
    >
      <div>
        <v-list-item-title class="menu-list">
          {{ $t('header_'+item) }}
        </v-list-item-title>
      </div>
    </v-list-item>
  </v-list>
</template>

<style scoped lang="scss">
@import '../sidenav-style';
</style>

<script>
import { useLocalePath } from '#imports';
import mega from '../data/mega';

export default {
  props: {
    home: {
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
  setup() {
    const localePath = useLocalePath();
    return {
      localePath,
    };
  },
  data() {
    return {
      menuList: mega,
      isOpen: false,
    };
  },
};
</script>
