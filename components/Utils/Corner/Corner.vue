<template>
  <page-nav v-if="type === 'nav'" :menu="menu" :prefix="prefix" />
  <chat v-if="type === 'chat'" />
</template>

<script setup>
import { toRefs } from 'vue';
import ui from '@/composables/uiTheme';
import PageNav from './PageNav';
import Chat from './Chat';

const type = ui.corner();
const props = defineProps({
  menu: {
    type: Array,
    required: true,
  },
  prefix: {
    type: String,
    default: 'ai-landing',
  },
});

const { menu, prefix } = toRefs(props);
</script>
