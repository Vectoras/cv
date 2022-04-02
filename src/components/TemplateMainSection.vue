<template>
  <section class="cv-main-section">
    <div class="vertical-line"></div>
    <header>
      <!-- Icon -->
      <!-- <div><font-awesome-icon :icon="sectionIcon" /></div> -->
      <!-- <div><font-awesome-icon :icon="['fas', 'user']" /></div> -->
      <i :class="sectionIcon"></i>

      <!-- Title -->
      <h3>{{ sectionTitle }}</h3>
      <div class="horizontal-line"></div>
    </header>

    <!-- Low Level Component Place -->
    <slot />
  </section>
</template>

<script>
  export default {
    name: 'MainSectionTemplate',
    props: {
      sectionTitle: {
        type: String,
        required: true,
      },
      sectionIcon: {
        // type: Array,
        type: String,
        required: true,
      },
    },
  };
</script>

<style lang="less" scoped>
  @import '../less/style_config';

  .cv-main-section {
    background: @color_ll_section_bg;
  }
</style>
