<script setup>
  import AboutViews from '@/views/AboutViews.vue';
  import ExperiencesView from '@/views/ExperiencesView.vue';
  import ProjectsViews from './views/ProjectsViews.vue';
  import ContactsViews from '@/views/ContactsViews.vue';
</script>

<template>
  <AboutViews :class="$style.item" />
  <ExperiencesView :class="$style.item" />
  <ProjectsViews :class="$style.item" />
  <ContactsViews :class="$style.item" />
</template>

<style module lang="scss">
  .item {
    margin-bottom: 4rem;
    @media (min-width: $tablet-size-land) {
      margin-bottom: 8rem;
    }
  }
</style>
