/* eslint-disable vue/require-v-for-key */
<template>
  <article class="cv-low-level-section">
    <header>
      <h4>{{ activityTitle }}</h4>
      <div>{{ organisationName }}, {{ organisationLocation }}</div>
      <div>
        <a :href="organisationWebsite" target="_blank">
          {{ organisationWebsite }}
        </a>
      </div>
      <div>{{ timeInterval }}</div>
    </header>
    <main>
      <p v-for="paragraph in jobDescription" :key="paragraph">
        {{ paragraph }}
      </p>
    </main>
  </article>
</template>

<script>
  import { toRefs, reactive, computed } from 'vue';

  export default {
    name: 'LowLevelActivitySection',
    props: {
      data: {
        type: Object,
        required: true,
      },
    },
    setup(props) {
      // !!!!!!! - they are not reactive to changes in components at higher level, could not figure out why
      const {
        activityTitle,
        organisationName,
        organisationWebsite,
        startDate,
        endDate,
        description,
        organisationCountry,
        organisationCounty,
        organisationCity,
      } = toRefs(reactive(props.data));

      const organisationLocation = computed(() => {
        let property = '';

        if (organisationCity.value)
          property = property ? `${property}, ${organisationCity.value}` : organisationCity.value;
        if (organisationCounty.value)
          property = property
            ? `${property}, ${organisationCounty.value}`
            : organisationCounty.value;
        if (organisationCountry.value)
          property = property
            ? `${property}, ${organisationCountry.value}`
            : organisationCountry.value;

        return property;
      });
      const jobDescription = computed(() => {
        return description.value.split('\n');
      });
      const timeInterval = computed(() => {
        if (startDate.value && endDate.value) return `${startDate.value} - ${endDate.value}`;

        return '';
      });

      return {
        activityTitle,
        organisationName,
        organisationLocation,
        organisationWebsite,
        timeInterval,
        jobDescription,
      };
    },
  };
</script>

<style></style>
