<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>Alexprogramma</q-toolbar-title>

        
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header>Ik krijg dit ding niet weg</q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue';
import EssentialLink from 'components/EssentialLink.vue';

const linksList = [
  {
    title: 'Leren',
    caption: 'Klik hier niet op',
    icon: 'school',
    link: 'https://nos.nl',
  },
  {
    title: 'Code',
    caption: 'Klik hier niet op',
    icon: 'code',
    link: '',
  },
  {
    title: 'Chatten',
    caption: 'Klik hier niet op',
    icon: 'chat',
    link: '',
  },
  {
    title: 'Forum',
    caption: 'Klik hier niet op',
    icon: 'record_voice_over',
    link: '',
  },
  {
    title: 'Twitter',
    caption: 'Klik hier niet op',
    icon: 'rss_feed',
    link: '',
  },
  {
    title: 'Facebook',
    caption: 'Klik hier niet op',
    icon: 'public',
    link: '',
  },
  {
    title: 'Like',
    caption: 'Klik hier niet op',
    icon: 'favorite',
    link: '',
  },
];

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
