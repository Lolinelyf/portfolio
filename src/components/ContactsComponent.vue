<script setup>
  const props = defineProps({
    path: {
      type: String,
      required: true,
    },
  });

  function alt(el) {
    return el.split('/').pop().split('.').shift();
  }
</script>

<template>
  <a href="" :class="$style.link"
    ><img :class="$style.item" :src="props.path" :alt="alt(props.path)"
  /></a>
</template>

<style module lang="scss">
  .link {
    display: block;
    width: 40px;
    height: 40px;
    margin-right: 1rem;
  }
  .item {
    width: 40px;
    height: 40px;
    filter: grayscale(1) invert(1);
    transition: filter ease 0.25s;

    &:hover {
      filter: grayscale(0) invert(0);
    }
  }
</style>
