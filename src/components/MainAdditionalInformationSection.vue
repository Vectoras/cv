<template>
  <template-main-section :sectionTitle="'Additional Information'" :sectionIcon="'fa-solid fa-info'">
    <low-level-text-section :data="additionalInformation" />
  </template-main-section>
</template>

<script>
  // importing components
  import TemplateMainSection from './TemplateMainSection.vue';
  import LowLevelTextSection from './LowLevelTextSection.vue';
  // import functionality
  import { toRef } from 'vue';

  export default {
    name: 'AdditionalInformationSection',
    components: { TemplateMainSection, LowLevelTextSection },
    props: {
      data: {
        type: String,
        required: true,
      },
    },
    setup(props) {
      const additionalInformation = toRef(props, 'data');

      return { additionalInformation };
    },
  };
</script>

<style></style>
