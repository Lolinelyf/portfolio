<script setup>
  const props = defineProps({
    path: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
  });

  function alt(el) {
    return el.split('/').pop().split('.').shift();
  }
</script>

<template>
  <div :class="$style.skill">
    <img :class="$style.lang" :src="props.path" :alt="alt(props.path)" />
    <p>{{ props.text }}</p>
  </div>
</template>

<style module lang="scss">
  .skill {
    display: flex;
    align-items: center;
    margin-right: 3rem;
    font-size: 1rem;
    font-weight: 400;

    & > p {
      margin: 0;
    }
  }
  .lang {
    margin-right: 2rem;
    filter: grayscale(1);
    transition: filter ease 0.25s;
    margin-right: 1rem;

    &:hover {
      filter: grayscale(0);
    }
  }
</style>
