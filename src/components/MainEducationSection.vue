<template>
  <!-- <template-main-section :sectionTitle="'Education'" :sectionIcon="['fas', 'graduation-cap']"> -->
  <template-main-section :sectionTitle="'Education'" :sectionIcon="'fas fa-graduation-cap'">
    <low-level-activity-section
      v-for="(activity, index) in activities"
      :key="`${index}-${activity.organisationName}`"
      :data="activity"
    />
  </template-main-section>
</template>

<script>
  // importing components
  import TemplateMainSection from './TemplateMainSection.vue';
  import LowLevelActivitySection from './LowLevelActivitySection.vue';
  // importing funcitonality
  import { reactive, ref, toRef, computed } from 'vue';

  export default {
    name: 'EducationSection',
    components: { TemplateMainSection, LowLevelActivitySection },
    props: {
      data: {
        type: Array,
        required: true,
      },
    },
    setup(props) {
      const education = toRef(props, 'data');

      const activities = computed(() => {
        let property = education.value.map((educationExperience) => {
          return reactive({
            activityTitle: ref(educationExperience.qualification),
            organisationName: ref(educationExperience.institutionName),
            organisationWebsite: ref(educationExperience.institutionWebsite),
            startDate: ref(educationExperience.startDate),
            endDate: ref(educationExperience.endDate),
            description: ref(educationExperience.description),
            organisationCountry: ref(educationExperience.institutionCountry),
            organisationCounty: ref(educationExperience.institutionCounty),
            organisationCity: ref(educationExperience.institutionCity),
          });
        });

        return property;
      });

      return { activities };
    },
  };
</script>

<style></style>
