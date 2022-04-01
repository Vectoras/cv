<template>
  <template-main-section :sectionTitle="'Skills'" :sectionIcon="'fa-solid fa-flask-vial'">
    <low-level-columns-list-section :data="skills" />
  </template-main-section>
</template>

<script>
  // import components
  import LowLevelColumnsListSection from './LowLevelListColumns.vue';
  import TemplateMainSection from './TemplateMainSection.vue';
  // import functionality
  import { toRef } from 'vue';

  export default {
    name: 'SkillsSection',
    components: { TemplateMainSection, LowLevelColumnsListSection },
    props: {
      data: {
        type: Array,
        required: true,
      },
    },
    setup(props) {
      const skills = toRef(props, 'data');

      return { skills };
    },
  };
</script>

<style></style>
