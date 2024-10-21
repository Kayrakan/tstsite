<template>
  <v-theme-provider
    :theme="themeMode || defaultMode"
    with-background
  >
    <div :class="theme">
      <v-locale-provider :rtl="isRtl()" :dir="isRtl() ? 'rtl' : 'ltr'">
        <slot />
      </v-locale-provider>
      <!--<theme-palette />-->
    </div>
  </v-theme-provider>
</template>

<script setup>
import { ref, onMounted, toRefs } from 'vue';
import { useI18n } from 'vue-i18n';
import ui from '@/composables/uiTheme';

const props = defineProps({
  theme: {
    type: String,
    required: true,
  },
});

const { theme } = toRefs(props);

// RTL Setup
const i18nLocale = useI18n();
const rtlDefault = i18nLocale.locale.value === 'ar';
const rtl = ui.rtl();
const isRtl = () => {
  if (rtl.value !== undefined) {
    return rtl.value;
  }
  return rtlDefault;
};

// Dark Light Setup
const defaultMode = ref('');
const themeMode = ui.themeMode();

onMounted(() => {
  // Set theme
  defaultMode.value = localStorage.getItem('bungalionTheme') || 'dark';
});
</script>
