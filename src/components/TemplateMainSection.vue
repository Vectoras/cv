<template>
  <section class="cv-main-section">
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
    padding-bottom: 1px; // margin collapse management
    padding-top: 1px; // margin collapse management

    .horizontal-line {
      position: absolute;
      top: 50%;
      z-index: -1;
      height: 0;
      width: 100%;
      border: none;
      border-top: solid @thikness_lines_m_section @color_lines_m_section;
    }

    &-header {
      position: relative;

      &-title {
        background: @color_bg_app;
        display: flex;
        flex-flow: row nowrap;
        align-items: center;
        gap: (@padding_title_m_section * 0.7);
        width: max-content;
        // min-height: @min_height_header_m_section;
        padding: 0.5rem @padding_title_m_section;
        margin-left: @distance_left_title_m_section;
        margin-top: @distance_top_title_m_section;
        margin-bottom: @distance_bottom_title_m_section;

        h3 {
          font-family: @font_family_header_m_section;
          font-size: @font_size_header_m_section;
          font-weight: @font_weight_header_m_section;
          text-transform: uppercase;
          color: @font_color_header_m_section;
        }

        i {
          display: inline-block;
          min-height: (@font_size_header_m_section * @incon_text_ratio_header_m_section);
          font-size: (@font_size_header_m_section * @incon_text_ratio_header_m_section);
          color: @color_icon_header_lls_activity;
        }
      }
    }

    // applies to lower components
    .cv-low-level-section {
      background: @color_bg_ll_section;
      padding: @padding_ll_section;
      margin-left: @distance_left_ll_section;
      margin-right: @distance_right_ll_section;
      margin-bottom: @distance_in_between_ll_section;

      font-family: @font_family_text_ll_section;
      font-size: @font_size_text_ll_section;
      font-weight: @font_weight_text_ll_section;
      line-height: @line_height_text_ll_section;
      color: @font_color_text_ll_section;

      box-shadow: 0 0 1rem shade(@color_main_bg, 15%);
    }
  }
</style>
