<template>
  <div class="app-container">
    <app-header :data="personalDetails" />
    <skills-section :data="skills" />
    <professional-summary-section :data="professionalSummary" />
    <portfolio-section :data="portfolio" />
    <work-history-section :data="workHistory" />
    <education-section :data="education" />
    <additional-information-section :data="additionalInformation" />
    <hobbies-section :data="hobbies" />
  </div>
</template>

<script>
  // import components
  import AppHeader from './components/MainHeaderSection.vue';
  import SkillsSection from './components/MainSkillsSection.vue';
  import ProfessionalSummarySection from './components/MainProfessionalSummarySection.vue';
  import PortfolioSection from './components/MainPortfolioSection.vue';
  import WorkHistorySection from './components/MainWorkHistorySection.vue';
  import EducationSection from './components/MainEducationSection.vue';
  import HobbiesSection from './components/MainHobbiesSection.vue';
  import AdditionalInformationSection from './components/MainAdditionalInformationSection.vue';
  // import data
  import rawData from './assets/data.json';
  // import functionality
  import { reactive, toRefs } from 'vue';

  export default {
    name: 'OnlineCvApp',
    components: {
      AppHeader,
      SkillsSection,
      ProfessionalSummarySection,
      PortfolioSection,
      WorkHistorySection,
      EducationSection,
      HobbiesSection,
      AdditionalInformationSection,
    },
    setup() {
      const {
        personalDetails,
        skills,
        professionalSummary,
        portfolio,
        workHistory,
        education,
        additionalInformation,
        hobbies,
      } = toRefs(reactive(rawData));

      return {
        personalDetails,
        skills,
        professionalSummary,
        portfolio,
        workHistory,
        education,
        additionalInformation,
        hobbies,
      };
    },
  };
</script>

<style lang="less">
  @import './less/style_config';

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    background: @color_bg_app;
    font-family: @font_family_app, @font_backup_style_app;
  }

  .app-container {
    max-width: @max_width_app;
    margin: 0 auto;
  }
</style>
