<script setup>
  import { ref } from 'vue';
  import { useIntersectionObserver } from '@vueuse/core';

  const props = defineProps({
    name: {
      type: String,
      required: true,
    },
    text: {
      type: String,
      required: true,
    },
    img: {
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

  const target = ref(null);
  const isActive = ref(false);

  if (window.matchMedia('(max-width: 576px)').matches) {
    const options = {
      rootMargin: '-15% 0px 0px 0px',
      threshold: 0.1,
    };
    useIntersectionObserver(
      target,
      ([{ isIntersecting }]) => {
        isActive.value = isIntersecting;
      },
      options,
    );
  }
</script>

<template>
  <a
    :class="{ [$style.card]: true, [$style.active]: isActive }"
    :href="props.link"
    ref="target"
  >
    <div :class="$style.blur">
      <img :class="$style.img" :src="props.img" :alt="alt(props.img)" />
    </div>

    <div :class="$style.detail">
      <section :class="$style.header">
        <h2 :class="$style.name">{{ props.name }}</h2>
        <div :class="$style.text">
          <p>
            {{ props.text }}
          </p>
        </div>
      </section>
      <div :class="$style.link">
        <img :class="$style.icon" src="/img/link.png" alt="link" />
        <p>Look it up</p>
      </div>
    </div>
  </a>
</template>
<style module lang="scss">
  .card {
    flex: 0 0 100%;
    background-color: var(--color-grey-a);
    box-shadow: var(--shadow-small-default);
    border-radius: 0.5rem;
    overflow: hidden;
    transition: box-shadow cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.5s;

    &:not(:last-child) {
      margin-bottom: 2rem;
    }

    @media (min-width: $mobile-size-land) {
      flex: 0 0 calc((100% - 8px) / 2);
      &:not(:last-child) {
        margin-bottom: 0.5rem;
      }
      margin-bottom: 0.5rem;
      transform: translateY(0);
      &:not(:nth-child(2n)) {
        margin-right: 8px;
      }
      cursor: pointer;

      &:active {
        background-color: #202020;
      }
    }

    @media (min-width: $tablet-size-port) {
      flex: 0 0 calc((100% - 16px) / 3);
      &:not(:nth-child(2n)) {
        margin-right: 0;
      }
      &:not(:nth-child(3n)) {
        margin-right: 8px;
      }

      &:hover .blur::after {
        opacity: 0;
      }
      &:hover .detail {
        transform: translateY(1rem);
      }

      &:hover .link {
        color: var(--color-accent);
      }
    }

    @media (min-width: $desktop-size-small) {
      flex: 0 0 calc((100% - 24px) / 4);
      &:not(:nth-child(3n)) {
        margin-right: 0;
      }
      &:not(:nth-child(4n)) {
        margin-right: 8px;
      }
    }
  }
  .blur {
    position: relative;
    &::after {
      content: '';
      position: absolute;
      display: block;
      width: 100%;
      height: 100%;
      bottom: 0;
      left: 0;
      background: linear-gradient(0deg, #1a1a1a 0%, #1a1a1aea 100%);
      opacity: 1;
      transition: opacity cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.5s;

      @media (min-width: $mobile-size-land) {
        background: linear-gradient(0deg, #1a1a1a 0%, #1a1a1aab 100%);
        transition: opacity cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.25s;
      }
    }
  }
  .img {
    display: block;
    width: 100%;
    height: 160px;
    object-fit: cover;
    // transition: opacity cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.5s;

    // @media (min-width: $mobile-size-land) {
    //   transition: opacity cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.25s;
    // }
  }

  .detail {
    display: flex;
    height: calc(100% - 160px);
    flex-flow: column wrap;
    justify-content: space-between;
    box-sizing: border-box;
    padding: 1rem;
    transition: transform cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.5s;

    @media (min-width: $mobile-size-land) {
      padding: 0 1rem 2rem;
      transition: transform cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.25s;
    }
  }

  .name {
    font-size: 1.2rem;
    font-weight: 500;
    color: var(--color-accent);
    letter-spacing: 0;

    @media (min-width: $mobile-size-land) {
      font-size: 1.4rem;
    }
  }

  .text {
    font-size: 0.9rem;
    font-weight: 400;
    color: var(--color-text-dusk);
    letter-spacing: 0;
    margin-bottom: 1rem;

    @media (min-width: $mobile-size-land) {
      font-weight: 500;
    }
  }

  .link {
    font-size: 0.9rem;
    font-weight: 400;
    color: var(--color-text-light);
    letter-spacing: 0;
    transition: color cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.5s;

    @media (min-width: $mobile-size-land) {
      transition: color cubic-bezier(0.23, 0.51, 0.63, 0.98) 0.25s;
    }

    & > p {
      display: inline-block;
      margin-bottom: 0;
      text-decoration: underline;
    }
  }

  .icon {
    width: 12px;
    height: 12px;
    margin-right: 0.5rem;
  }

  .active {
    box-shadow: -2px 4px 16px 2px #152317;

    & .blur::after {
      opacity: 0;
    }

    & .link {
      color: var(--color-accent);
    }
  }
</style>
