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
    width: 32px;
    height: 32px;
    margin-right: 0.5rem;
    @media (min-width: $tablet-size-land) {
      width: 40px;
      height: 40px;
      margin-right: 1rem;
    }
  }
  .item {
    width: 32px;
    height: 32px;
    border-radius: 100%;
    filter: grayscale(0) invert(0);
    transition: filter ease 0.1s;

    &:active {
      filter: grayscale(1) invert(1);
    }

    @media (min-width: $tablet-size-land) {
      width: 40px;
      height: 40px;
      filter: grayscale(1) invert(1);
      transition: filter ease 0.25s;
      &:active {
        box-shadow: var(--shadow-small-default);
      }

      &:hover {
        filter: grayscale(0) invert(0);
      }
    }
  }
</style>
