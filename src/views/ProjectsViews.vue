<script setup>
  import { onMounted } from 'vue';
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
<style module lang="scss">
  .flex {
    display: flex;
    flex-flow: row wrap;
    margin-bottom: 4rem;

    @media (min-width: $tablet-size-port) {
      margin-bottom: 8rem;
    }
  }
</style>
