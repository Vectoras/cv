<template>
  <section class="cv-main-section">
    <div class="vertical-line"></div>
    <header>
      <!-- Icon -->
      <!-- <div><font-awesome-icon :icon="sectionIcon" /></div> -->

      <!-- Title -->
      <h3>{{ sectionTitle }}</h3>
      <div class="horizontal-line"></div>
    </header>

    <!-- Low Level Component Place -->
    <slot></slot>
  </section>
</template>

<script>
  export default {
    name: 'MainSectionTemplate',
    props: {
      sectionTitle: {
        type: String,
        required: true,
      },
      sectionIcon: {
        type: String,
        required: true,
      },
    },
  };
</script>

<style></style>
