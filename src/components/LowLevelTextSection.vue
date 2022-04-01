<template>
  <div class="cv-low-level-section">
    <p v-for="paragraph in paragraphs" :key="paragraph">
      {{ paragraph }}
    </p>
  </div>
</template>

<script>
  import { computed } from 'vue';
  export default {
    name: 'LowLevelTextSection',
    props: {
      data: {
        type: String,
        required: true,
      },
    },
    setup(props) {
      const paragraphs = computed(() => {
        return props.data.split('\n');
      });

      return { paragraphs };
    },
  };
</script>

<style></style>
