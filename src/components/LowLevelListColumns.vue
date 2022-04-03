<template>
  <article class="cv-low-level-section cv-ll-list-columns">
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

<style lang="less">
  @import '../less/style_config';

  .cv-ll-list-columns {
    ul {
      list-style-type: none;
      display: flex;
      flex-flow: row wrap;

      li {
        width: 25%;
        padding: 0.5rem 1rem;
      }
    }
  }
</style>
