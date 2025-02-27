<template>
  <div class="navigation">
    <nav class="nav-menu">
      <span>
        <a
          v-smooth-scroll="{ offset: 100 }"
          href="#home"
          class="logo anchor-link scrollactive-item"
        >
          <img :src="brand.img" alt="logo">
        </a>
      </span>
      <v-list nav class="menu">
        <ul>
          <v-list-item
            v-for="(item, index) in menuList"
            :key="index"
            :href="item.url"
            :class="{ active: activeMenu === item.name }"
            class="link anchor-link"
            @click="scrollToMyEl(item.name)"
          >
            <span class="darken" />
            <span class="deco" />
            <div class="icon">
              <span :class="item.icon" />
            </div>
            <v-list-item-title class="text">
              {{ $t('profile.header_' + item.name) }}
            </v-list-item-title>
          </v-list-item>
        </ul>
      </v-list>
    </nav>
  </div>
</template>

<style lang="scss" scoped>
@import './sidenav-style.scss';
</style>

<script setup>
import {
  inject, onMounted,
  ref, toRefs,
} from 'vue';
import brand from '@/assets/text/brand';
import { useRouter } from '#app';

const props = defineProps({
  navMenu: {
    type: Array,
    required: true,
  },
});

const { navMenu } = toRefs(props);

let counter = 0;
function createData(name, url, icon, offset) {
  counter += 1;
  return {
    id: counter,
    name,
    url,
    icon,
    offset,
  };
}

const smoothScroll = inject('smoothScroll');
function scrollToMyEl(elemId) {
  const myEl = document.getElementById(elemId);
  const router = useRouter();

  router.push(`#${elemId}`);
  smoothScroll({
    scrollTo: myEl, // scrollTo is also allowed to be number
    hash: `#${elemId}`, // required if updateHistory is true
    offset: -100,
  });
}

const loaded = ref(false);
const sections = ref({});
const activeMenu = ref('');
const menuList = ref([
  createData(navMenu.value[0].name, '#' + navMenu.value[0].id, 'ion-ios-contact-outline', 160),
  createData(navMenu.value[1].name, '#' + navMenu.value[1].id, 'ion-ios-analytics-outline'),
  createData(navMenu.value[2].name, '#' + navMenu.value[2].id, 'ion-ios-keypad-outline'),
  createData(navMenu.value[3].name, '#' + navMenu.value[3].id, 'ion-ios-chatboxes-outline', -40),
  createData(navMenu.value[4].name, '#' + navMenu.value[4].id, 'ion-ios-paper-outline'),
  createData(navMenu.value[5].name, '#' + navMenu.value[5].id, 'ion-ios-mail-outline'),
]);

onMounted(() => {
  loaded.value = true;
  const id = window.location.hash;
  const content = id.replace('#', '');
  const element = document.getElementById(content);
  if (element) {
    element.scrollIntoView();
  }

  const section = document.querySelectorAll('.scroll-nav-content > *');
  Array.prototype.forEach.call(section, (e) => {
    sections.value[e.id] = e.offsetTop;
  });
});
</script>
