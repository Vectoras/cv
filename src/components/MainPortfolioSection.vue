<template>
  <!-- <template-main-section :sectionTitle="'Portfolio'" :sectionIcon="['fas', 'flask-vial']"> -->
  <template-main-section :sectionTitle="'Portfolio'" :sectionIcon="'fas fa-flask'">
    <low-level-simple-list-section :data="urls" />
  </template-main-section>
</template>

<script>
  // importing components
  import TemplateMainSection from './TemplateMainSection.vue';
  import LowLevelSimpleListSection from './LowLevelListSimple.vue';
  // importing funcitonality
  import { toRef } from 'vue';

  export default {
    name: 'PortfolioSection',
    components: { TemplateMainSection, LowLevelSimpleListSection },
    props: {
      data: {
        type: Array,
        required: true,
      },
    },
    setup(props) {
      const urls = toRef(props, 'data');

      return { urls };
    },
  };
</script>

<style></style>
