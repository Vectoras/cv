<template>
  <footer class="cv-footer"></footer>
</template>

<script>
  export default {
    name: 'FooterSection',
  };
</script>

<style lang="less">
  @import '../less/style_config';

  .cv-footer {
    position: relative;
    min-height: @min_height_app_footer;
    box-shadow: 0 0 1rem shade(@color_main_bg, 20%);
    background-color: @color_bg_app_footer;

    &::before {
      content: '';
      display: block;
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;

      background-image: url(@image_bg_app_header);
      background-position: center center;
      background-repeat: no-repeat;
      background-size: cover;
      // filter: opacity(0.9);
    }

    &::after {
      content: '';
      position: absolute;
      top: 0;
      right: 0;
      bottom: 0;
      left: 0;

      // background-color: rgba(255, 255, 255, 0.1);

      // background-image: linear-gradient(
      //   180deg,
      //   darken(@color_bg_app_header, 10%) 0%,
      //   // @color_bg_app_header 10%,
      //   // transparent 0%,
      //   // transparent 65%,
      //   transparent 60%
      // );
    }

    // top distance done in cv-body in App component as a bottom-padding
  }
</style>
