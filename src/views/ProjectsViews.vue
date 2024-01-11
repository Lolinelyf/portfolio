<script setup>
  import CardProjectComponent from '@/components/CardProjectComponent.vue';
  import { getProjectItems } from '@/api/Projects';
</script>
<template>
  <div class="container">
    <h1>Projects</h1>
    <div :class="$style.flex">
      <CardProjectComponent
        v-for="project in getProjectItems()"
        :key="project.id"
        :name="project.name"
        :text="project.text"
        :img="project.img"
        :link="project.link"
      />
    </div>
  </div>
</template>
<style module>
  .flex {
    display: flex;
    flex-flow: row wrap;
  }
</style>
