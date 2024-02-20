<script setup>
  const props = defineProps({
    path: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
  });

  function alt(el) {
    return el.split('/').pop().split('.').shift();
  }
</script>

<template>
  <a :href="props.link" :class="$style.link"
    ><img :class="$style.item" :src="props.path" :alt="alt(props.path)"
  /></a>
</template>

<style module lang="scss">
  .link {
    display: block;
    width: 30px;
    height: 30px;

    &:not(:last-child) {
      margin-right: 0.6rem;
    }

    @media (min-width: $tablet-size-land) {
      width: 40px;
      height: 40px;
      &:not(:last-child) {
        margin-right: 1rem;
      }
    }
  }
  .item {
    width: 30px;
    height: 30px;
    border-radius: 100%;

    &[alt='git'] {
      filter: grayscale(1) invert(1);
    }

    &:active {
      opacity: 0.6;
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
