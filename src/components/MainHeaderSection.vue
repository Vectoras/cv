<template>
  <header class="cv-header">
    <!-- left column -->
    <div class="cv-header-name">
      <h1>{{ fullName }}</h1>
      <h2>{{ jobTitle }}</h2>
    </div>

    <!-- right column -->
    <address class="cv-header-details">
      <p>{{ fullAddress }}</p>
      <p>{{ phone }}</p>
      <p>{{ email }}</p>
      <p>
        <a :href="website" target="_blank" rel="external">{{ website }}</a>
      </p>
    </address>
  </header>
</template>

<script>
  import { reactive, toRefs, computed } from 'vue';

  export default {
    name: 'HeaderSection',
    props: {
      data: {
        type: Object,
        required: true,
      },
    },
    setup(props) {
      const { city, county, country, fullName, jobTitle, phone, email, website } = toRefs(
        reactive(props.data)
      );

      const fullAddress = computed(() => {
        let property = '';

        if (city.value) property = property ? `${property}, ${city.value}` : city.value;
        if (county.value) property = property ? `${property}, ${county.value}` : county.value;
        if (country.value) property = property ? `${property}, ${country.value}` : country.value;

        return property;
      });

      return { fullAddress, fullName, jobTitle, phone, email, website };
    },
  };
</script>

<style lang="less">
  @import '../less/style_config';

  .cv-header {
    background: @color_bg_app_header;
    background-image: linear-gradient(
        0deg,
        transparent 0%,
        @color_bg_app_header 0%,
        @color_bg_app_header 48%,
        transparent 65%,
        transparent 100%
      ),
      url(@image_bg_app_header);
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;

    box-shadow: 0 0 1rem shade(@color_main_bg, 20%);

    padding: @padding_app_header;
    padding-bottom: @distance_bottom_app_header;

    display: flex;
    flex-flow: row nowrap;
    justify-content: space-around;
    align-items: flex-end;
    min-height: @min_height_app_header;

    h1 {
      font-family: @font_family_name_app_header;
      font-size: @font_size_name_app_header;
      font-weight: @font_weight_name_app_header;
      color: @font_color_name_app_header;
    }

    h2 {
      font-family: @font_family_job_app_header;
      font-size: @font_size_job_app_header;
      font-weight: @font_weight_job_app_header;
      color: @font_color_job_app_header;
    }

    address {
      font-style: normal;
      font-size: @font_size_details_app_header;
      font-weight: @font_weight_details_app_header;
      font-family: @font_family_details_app_header;
      color: @font_color_details_app_header;

      p {
        margin-top: 0.5rem;
      }
    }
  }
</style>
