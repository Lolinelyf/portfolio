<script setup></script>
<template>
  <div class="container">
    <h1>Experience</h1>
    <div :class="$style.flex">
      <div :class="$style.experience">
        <h2 :class="$style.title">Большой опыт работы</h2>
        <ul>
          <li>Vue js</li>
          <li>JavaScript</li>
          <li>Api</li>
          <li>Router</li>
          <li>Git, GitHub</li>
        </ul>
      </div>
      <div :class="$style.experience">
        <h2 :class="$style.title">Работаю и изучаю</h2>
        <ul>
          <li>CSS Preprocessors</li>
          <li>Figma</li>
          <li>Pinia</li>
          <li>Content manager</li>
          <li>LeetCode</li>
        </ul>
      </div>
      <div :class="$style.experience">
        <h2 :class="$style.title">Был опыт работы</h2>
        <ul>
          <li>1C Битрикс</li>
          <li>Создание Brand and Logo</li>
          <li>Figma</li>
          <li>Testing</li>
          <li>Code review</li>
        </ul>
      </div>
    </div>
  </div>
</template>
<style module lang="scss">
  .flex {
    display: flex;
    flex-flow: row wrap;
    margin-bottom: 4rem;

    @media (min-width: $tablet-size-port) {
      flex-flow: row nowrap;
      margin-bottom: 8rem;
    }
  }
  .experience {
    flex: 0 0 100%;
    padding: 1rem;
    background-color: var(--color-grey-a);
    border-radius: 1rem;
    box-shadow: var(--shadow-small-default);
    &:not(:last-child) {
      margin-bottom: 1rem;
    }

    @media (min-width: $mobile-size-land) {
      flex: 0 0 calc((100% - 2rem) / 2);
      &:not(:last-child) {
        margin-bottom: 2rem;
      }
      margin-bottom: 2rem;

      &:not(:nth-child(2n)) {
        margin-right: 2rem;
      }
    }

    @media (min-width: $tablet-size-port) {
      flex: 0 0 calc((100% - 4rem) / 3);
      &:not(:nth-child(2n)) {
        margin-right: 0;
      }
      &:not(:last-child) {
        margin-right: 2rem;
      }
    }

    @media (min-width: $tablet-size-land) {
      padding: 2rem;
    }
  }

  .title {
    font-size: 1rem;
    font-weight: 600;
    margin-bottom: 1rem;
    @media (min-width: $tablet-size-land) {
      font-size: 1.2rem;
      margin-bottom: 2rem;
    }
  }
</style>
