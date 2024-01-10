<script setup>
  import AboutViews from '@/views/AboutViews.vue';
  import ExperiencesView from '@/views/ExperiencesView.vue';
  import ContactsViews from '@/views/ContactsViews.vue';
</script>

<template>
  <AboutViews :class="$style.item" />
  <ExperiencesView :class="$style.item" />
  <ContactsViews :class="$style.item" />
</template>

<style module>
  .item {
    margin-bottom: 10rem;
  }
</style>
