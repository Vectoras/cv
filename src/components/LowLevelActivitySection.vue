/* eslint-disable vue/require-v-for-key */
<template>
  <article class="cv-low-level-section cv-ll-activity">
    <header class="cv-ll-activity-header">
      <h4 class="cv-ll-activity-header-title">{{ activityTitle }}</h4>

      <div class="cv-ll-activity-header-organisation">
        <span>{{ organisationName }}</span
        >{{ organisationLocation }}
      </div>

      <div>
        <a :href="organisationWebsite" target="_blank">
          {{ organisationWebsite }}
        </a>
      </div>
      <div class="cv-ll-activity-header-time">{{ timeInterval }}</div>
    </header>
    <main class="cv-ll-activity-content">
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
          property = property
            ? `${property}, ${organisationCity.value}`
            : `, ${organisationCity.value}`;
        if (organisationCounty.value)
          property = property
            ? `${property}, ${organisationCounty.value}`
            : `, ${organisationCounty.value}`;
        if (organisationCountry.value)
          property = property
            ? `${property}, ${organisationCountry.value}`
            : `, ${organisationCountry.value}`;

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

<style lang="less">
  @import '../less/style_config';

  .cv-ll-activity {
    &-header {
      display: grid;
      grid-template-columns: repeat(2, auto);
      margin-bottom: @distance_header_content_lls_activity;
      font-size: @font_size_header_lls_activity;
      font-family: @font_family_header_lls_activity;
      font-weight: @font_weight_header_lls_activity;

      &-title {
        text-transform: uppercase;
        font-family: @font_family_title_lls_activity;
        font-weight: @font_weight_title_lls_activity;
        font-size: @font_size_title_lls_activity;
      }

      &-organisation {
        span {
          font-family: @font_family_title_lls_activity;
          font-weight: @font_weight_organisation_lls_activity;
        }
      }

      &-time {
        grid-column: 2 / span 1;
        grid-row: 1 / span 3;
        text-align: right;
      }
    }

    &-content {
    }
  }
</style>
