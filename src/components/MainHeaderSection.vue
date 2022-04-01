<template>
  <header class="cv-header">
    <!-- left column -->
    <div>
      <h1>{{ fullName }}</h1>
      <h2>{{ jobTitle }}</h2>
    </div>

    <!-- right column -->
    <address>
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

<style></style>
