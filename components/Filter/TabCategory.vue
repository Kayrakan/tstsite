<template>
  <div class="root-tab">
    <v-tabs
      v-model="valTab"
      class="tabs"
      :align-tabs="!isMobile ? 'center' : 'left'"
      @update:model-value="switchTab"
    >
      <v-tab class="tab-label" value="all">
        <span>All</span>
      </v-tab>
      <v-tab class="tab-label" value="items">
        <span>Items</span>
      </v-tab>
      <v-tab class="tab-label" value="collection">
        <span>Collection</span>
      </v-tab>
      <v-tab class="tab-label" value="creators">
        <span>Creators</span>
      </v-tab>
    </v-tabs>
    <h6 v-if="isTablet" :class="isDesktop ? 'use-text-subtitle2' : 'use-text-paragraph'">
      Show
      {{ total }}
      Results
    </h6>
  </div>
</template>

<style lang="scss" scoped>
@import './filter';
</style>

<script setup>
import { ref, toRefs } from 'vue';
import { useDisplay } from 'vuetify';

const props = defineProps({
  value: {
    type: String,
    required: true,
  },
  switchTab: {
    type: Function,
    required: true,
  },
  total: {
    type: Number,
    required: true,
  },
});

const { value, switchTab, total } = toRefs(props);

const { lgAndUp: isDesktop } = useDisplay();
const { mdAndUp: isTablet } = useDisplay();
const { smAndDown: isMobile } = useDisplay();

const valTab = ref(value);
</script>
