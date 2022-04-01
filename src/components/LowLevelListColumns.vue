<template>
  <article class="cv-low-level-section">
    <ul>
      <li v-for="(item, index) in list" :key="`${index}-${item}`">
        {{ item }}
      </li>
    </ul>
  </article>
</template>

<script>
  import { toRef } from 'vue';

  export default {
    name: 'LowLevelColumnsListSection',
    props: {
      data: {
        type: Array,
        required: true,
      },
    },
    setup(props) {
      const list = toRef(props, 'data');

      return { list };
    },
  };
</script>

<style></style>
