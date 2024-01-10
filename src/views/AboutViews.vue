<script setup>
  import SkillsComponent from '@/components/SkillsComponent.vue';
  import { getSkillsItem } from '@/api/Skills.js';
</script>
<template>
  <div class="container">
    <h1>Personal information</h1>
    <div :class="$style.about">
      <div :class="$style.info">
        <h2 :class="$style.title">Сергей Коваленко</h2>
        <div :class="$style.history">
          <p>
            Я более чем влюблен в Front-End. Мой опыт работы с дизайном
            интерфейсов делает меня крайне критичным к выравниванием, полями,
            цветами и многими другими ресурсами в CSS. Сегодня я работаю с
            проектами в целом мире. Кодирую в своем домашнем офисе, в тихом
            районе Сан-Паулу, Бразилия.
          </p>
        </div>
        <div :class="$style.skills">
          <SkillsComponent
            v-for="item in getSkillsItem()"
            :key="item.id"
            :path="item.path"
            :text="item.text"
          />
        </div>
      </div>
      <img :class="$style.me" src="/img/me.png" alt="me" />
    </div>
  </div>
</template>
<style module lang="scss">
  .about {
    display: flex;
    flex-flow: row;
    justify-content: space-between;
    align-items: center;
    letter-spacing: 2px;
  }

  .info {
    flex: 0 0 60%;
  }

  .title {
    color: var(--color-text-light);
  }

  .me {
    flex: 0 0 25%;
  }

  .history {
    font-size: 1.2rem;
    margin-bottom: 2rem;
    color: var(--color-text-dusk);
  }

  .skills {
    display: flex;
    align-items: center;
  }
</style>
