<template>
  <div class="line">
    <div class="deco">
      <svg class="primary">
        <use xlink:href="/images/decoration/wave.svg#main" />
      </svg>
      <svg class="secondary">
        <use xlink:href="/images/decoration/wave.svg#main" />
      </svg>
    </div>
    <div id="footer_deco">
      <slot />
    </div>
  </div>
</template>

<style lang="scss" scoped>
@import './decoration-style';
</style>
