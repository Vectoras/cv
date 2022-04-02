<template>
  <!-- <template-main-section
    :sectionTitle="'Professional Summary'"
    :sectionIcon="['fas', 'user-check']"
  > -->
  <template-main-section :sectionTitle="'Professional Summary'" :sectionIcon="'fas fa-user-check'">
    <low-level-text-section :data="professionalSummary" />
  </template-main-section>
</template>

<script>
  // importing components
  import TemplateMainSection from './TemplateMainSection.vue';
  import LowLevelTextSection from './LowLevelTextSection.vue';
  // importing funcitonality
  import { toRef } from 'vue';

  export default {
    name: 'ProfessionalSummarySection',
    components: { TemplateMainSection, LowLevelTextSection },
    props: {
      data: {
        type: String,
        required: true,
      },
    },
    setup(props) {
      const professionalSummary = toRef(props, 'data');

      return { professionalSummary };
    },
  };
</script>

<style></style>
