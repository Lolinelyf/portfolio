<script setup>
  import ContactsComponent from '@/components/ContactsComponent.vue';
  import { getContactsItem } from '@/api/Contacts.js';
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
          <a :class="$style.link" href="mailto:lolinelyf@mail.ru"
            >lolinelyf@mail.ru</a
          >
        </div>
      </div>
      <div :class="$style.social">
        <ContactsComponent
          v-for="item in getContactsItem()"
          :key="item.id"
          :path="item.path"
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
    width: 26px;
    height: 26px;
    object-fit: contain;
    margin-right: 1rem;
  }

  .link {
    color: var(--color-text-dusk);
    font-size: 0.9rem;
    font-weight: 600;
    transition: color ease 0.15s;

    &:hover {
      color: var(--color-text-light);
    }
  }
  .social {
    display: flex;
    margin-bottom: 1rem;
  }
</style>
