<template>
  <section class="cv-main-section">
    <div class="vertical-line"></div>
    <header class="cv-main-section-header">
      <div class="horizontal-line"></div>

      <div class="cv-main-section-header-title">
        <!-- Icon -->
        <!-- <div><font-awesome-icon :icon="sectionIcon" /></div> -->
        <!-- <div><font-awesome-icon :icon="['fas', 'user']" /></div> -->
        <i :class="sectionIcon"></i>

        <!-- Title -->
        <h3>{{ sectionTitle }}</h3>
      </div>
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

<style lang="less">
  @import '../less/style_config';

  .cv-main-section {
    position: relative;
    padding-left: calc(@distance_lines_horizontal_left + @thikness_lines_m_section);
    padding-bottom: 1px; // because of child margin

    .horizontal-line {
      position: absolute;
      top: 50%;
      z-index: -1;
      height: 0;
      width: 100%;
      border: none;
      border-top: solid @thikness_lines_m_section @color_lines_m_section;
    }

    .vertical-line {
      position: absolute;
      left: @distance_lines_horizontal_left;
      z-index: -1;
      width: 0;
      height: 100%;
      border: none;
      border-left: solid @thikness_lines_m_section @color_lines_m_section;
    }

    &-header {
      position: relative;

      &-title {
        background: @color_bg_app;
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        gap: 0.5rem;
        width: max-content;
        min-height: @height_header_m_section;
        padding: 0.5rem;
        margin-left: @distance_title_left_m_section;
      }
    }

    // applies to lower components
    .cv-low-level-section {
      background: @color_bg_ll_section;
      padding: @padding_ll_section;
      margin-left: @distance_left_ll_section;
      margin-right: @distance_right_ll_section;
      margin-bottom: @distance_in_between_ll_section;
    }
  }
</style>
