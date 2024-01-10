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
    flex-flow: row nowrap;
  }
  .experience {
    flex: 0 1 calc((100% - 4rem) / 3);
    padding: 2rem;
    background-color: var(--color-grey-c);
    border-radius: 1rem;
    box-shadow: var(--shadow-small-default);

    &:not(:last-child) {
      margin-right: 2rem;
    }
  }

  .title {
    font-size: 1.2rem;
    font-weight: 600;
    margin-bottom: 2rem;
  }
</style>
