<template>
  <!-- <template-main-section :sectionTitle="'Hobbies'" :sectionIcon="['fas', 'person-swimming']"> -->
  <template-main-section :sectionTitle="'Hobbies'" :sectionIcon="'fas fa-swimmer'">
    <low-level-text-section :data="hobbies" />
  </template-main-section>
</template>

<script>
  // importing components
  import TemplateMainSection from './TemplateMainSection.vue';
  import LowLevelTextSection from './LowLevelTextSection.vue';
  // import functionality
  import { toRef } from 'vue';

  export default {
    name: 'HobbiesSection',
    components: { TemplateMainSection, LowLevelTextSection },
    props: {
      data: {
        type: String,
        required: true,
      },
    },
    setup(props) {
      const hobbies = toRef(props, 'data');

      return { hobbies };
    },
  };
</script>

<style></style>
