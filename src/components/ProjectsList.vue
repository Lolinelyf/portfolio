<script setup>
  import CardProject from '@/components/CardProject.vue';
  import { onMounted, ref } from 'vue';

  const projectsList = ref([]);

  onMounted(() => {
    fetch('https://436e9db67f2dc527.mokky.dev/projects')
      .then((res) => res.json())
      .then((data) => (projectsList.value = data));
  });
</script>
<template>
  <div class="container">
    <h1>Projects</h1>
    <div :class="$style.flex">
      <CardProject
        v-for="project in projectsList"
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
