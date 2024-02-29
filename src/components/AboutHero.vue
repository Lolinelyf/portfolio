<script setup>
  import SkillsItem from "@/components/SkillsItem.vue";
  import { onMounted, ref } from "vue";
  const skillsList = ref([]);
  onMounted(async () => {
    try {
      const response = await fetch("https://436e9db67f2dc527.mokky.dev/skills");
      skillsList.value = await response.json();
    } catch (err) {
      console.log(err);
    }
  });
</script>
<template>
  <div class="container">
    <h1>Personal information</h1>
    <div :class="$style.about">
      <div :class="$style.info">
        <h2 :class="$style.title">Сергей Коваленко</h2>
        <div :class="$style.history">
          <p>
            Я начинающий Frontend-разработчик из красивого города Ставрополь,
            Россия.
          </p>
          <p>
            Моя страсть к коду зародилась более года назад, когда я впервые
            погрузился в мир веб-разработки. Мои главные принципы: создание
            эстетичных, интуитивно понятных пользовательских интерфейсов.
          </p>
          <p>
            Мой путь Frontend-разработчика только начинается. Я полон энтузиазма
            и готовности к постоянному росту.
          </p>
        </div>
        <div
          :class="$style.skills"
          v-if="skillsList"
        >
          <SkillsItem
            v-for="item in skillsList"
            :key="item.id"
            :path="item.path"
            :text="item.text"
          />
        </div>
      </div>
      <img
        :class="$style.me"
        src="/img/me.png"
        alt="me"
      />
    </div>
  </div>
</template>
<style module lang="scss">
  .about {
    display: flex;
    width: 100%;
    flex-flow: column;
    justify-content: space-between;
    align-items: center;
    letter-spacing: 2px;
    margin-bottom: 2rem;

    @media (min-width: $desktop-size-small) {
      flex-flow: row;
      align-items: center;
      lign-items: flex-start;
      margin-bottom: 8rem;
    }
  }

  .info {
    flex: 0 0 100%;
    width: 100%;
    margin-bottom: 2rem;
    @media (min-width: $tablet-size-port) {
      flex: 0 0 60%;
      width: 60%;
      margin-bottom: 0;
    }
  }

  .title {
    color: var(--color-text-light);
  }

  .me {
    flex: 0 0 22%;
    display: block;
    border-radius: 100%;
    overflow: hidden;
    width: 22%;

    @media (min-width: $desktop-size-small) {
      flex: 0 0 25%;
      width: 25%;
    }
  }

  .history {
    font-size: 0.9rem;
    margin-bottom: 2rem;
    color: var(--color-text-dusk);
    letter-spacing: 1px;

    @media (min-width: $tablet-size-port) {
      font-size: 1rem;
      letter-spacing: 2px;
    }

    @media (min-width: $tablet-size-land) {
      font-size: 1.2rem;
    }
  }

  .skills {
    display: flex;
    align-items: center;
    width: 100%;
  }
</style>
