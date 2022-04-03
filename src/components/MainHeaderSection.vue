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
      <p>{{ website }}</p>
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
    padding: @padding_app_header;
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-around;

    h1 {
      font-family: @font_family_name_app_header;
      font-size: 2.5rem;
      font-weight: 700;
    }

    h2 {
      font-family: @font_family_job_app_header;
      // font-size: 2.5rem;
      font-weight: 400;
    }

    address {
      font-style: normal;
      font-family: @font_family_details_app_header;
    }
  }
</style>
