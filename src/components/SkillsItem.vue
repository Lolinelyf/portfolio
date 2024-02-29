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
    return el.split("/").pop().split(".").shift();
  }
</script>

<template>
  <div :class="$style.skill">
    <img
      :class="$style.lang"
      :src="props.path"
      :alt="alt(props.path)"
    />
    <p>{{ props.text }}</p>
  </div>
</template>

<style module lang="scss">
  .skill {
    display: flex;
    align-items: center;
    width: min-content;
    margin-right: 1rem;
    font-size: 0.8rem;
    font-weight: 400;
    line-height: 1.2;
    letter-spacing: 1px;

    @media (min-width: $tablet-size-port) {
      width: auto;
      font-size: 1rem;
      margin-right: 3rem;
      line-height: 1.4;
      letter-spacing: 2px;
    }

    & > p {
      margin: 0;
    }
  }
  .lang {
    width: 32px;
    height: 32px;
    margin-right: 0.5rem;

    @media (min-width: $tablet-size-port) {
      width: 48px;
      height: 48px;
      margin-right: 1rem;
      filter: grayscale(1);
      transition: filter ease 0.25s;

      &:hover {
        filter: grayscale(0);
      }
    }
  }
</style>
