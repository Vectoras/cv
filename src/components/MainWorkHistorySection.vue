<template>
  <!-- <template-main-section :sectionTitle="'Work History'" :sectionIcon="['fas', 'person-digging']"> -->
  <template-main-section :sectionTitle="'Work History'" :sectionIcon="'fas fa-hard-hat'">
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
    name: 'WorkHistorySection',
    components: { TemplateMainSection, LowLevelActivitySection },
    props: {
      data: {
        type: Array,
        required: true,
      },
    },
    setup(props) {
      const workHistory = toRef(props, 'data');

      const activities = computed(() => {
        let property = workHistory.value.map((workExperience) => {
          return reactive({
            activityTitle: ref(workExperience.jobTitle),
            organisationName: ref(workExperience.companyName),
            organisationWebsite: ref(workExperience.companyWebsite),
            startDate: ref(workExperience.startDate),
            endDate: ref(workExperience.endDate),
            description: ref(workExperience.description),
            organisationCountry: ref(workExperience.companyCountry),
            organisationCounty: ref(workExperience.companyCounty),
            organisationCity: ref(workExperience.companyCity),
          });
        });

        return property;
      });

      return { activities };
    },
  };
</script>

<style></style>
