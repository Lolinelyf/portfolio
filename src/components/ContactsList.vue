<script setup>
  import ContactsItem from '@/components/ContactsItem.vue';
  import { onMounted, ref } from 'vue';

  const contactsList = ref([]);
  onMounted(() => {
    fetch('https://436e9db67f2dc527.mokky.dev/Contacts')
      .then((res) => res.json())
      .then((data) => (contactsList.value = data));
  });
</script>
<template>
  <div class="container">
    <h1>Contacts</h1>
    <div :class="$style.flex">
      <div :class="$style.contacts">
        <div :class="$style.item">
          <img :class="$style.img" src="/img/tel.png" alt="tel" />
          <a :class="$style.link" href="tel:+79880908821">+7(988)090-88-21</a>
        </div>
        <div :class="$style.item">
          <img :class="$style.img" src="/img/mail.png" alt="mail" />
          <a :class="$style.link" href="mailto:job@lolinelyf.ru"
            >job@lolinelyf.ru</a
          >
        </div>
      </div>
      <div :class="$style.social">
        <ContactsItem
          v-for="item in contactsList"
          :key="item.id"
          :path="item.path"
          :link="item.link"
        />
      </div>
    </div>
  </div>
</template>
<style module lang="scss">
  .flex {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;
    align-items: flex-end;
    padding-bottom: 2rem;
  }
  .item {
    display: flex;
    align-items: center;
    margin-bottom: 1rem;
  }

  .img {
    width: 18px;
    height: 18px;
    object-fit: contain;
    margin-right: 1rem;
    @media (min-width: $tablet-size-land) {
      width: 24px;
      height: 24px;
    }
  }

  .link {
    color: var(--color-text-dusk);
    font-size: 0.8rem;
    font-weight: 500;

    &:active {
      color: var(--color-text-light);
    }

    @media (min-width: $tablet-size-land) {
      font-size: 0.9rem;
      ont-weight: 600;
      transition: color ease 0.15s;

      &:hover {
        color: var(--color-text-light);
      }
    }
  }
  .social {
    display: flex;
    margin-bottom: 1rem;
  }
</style>
