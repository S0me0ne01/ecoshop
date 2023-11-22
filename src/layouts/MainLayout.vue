<template>
  <q-layout view="lHh Lpr lFf" style="background-color: #4cff91">
    <!-- HEADER -->
    <q-header elevated>
      <q-toolbar style="background-color: #4cff91">
        <q-btn flat dense round icon="menu" aria-label="Menu" style="color: #000000" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          &nbsp;&nbsp;<a href="/"><img src="/images/logo.png" height="50" style="padding-top: 8px" /></a>
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-not-above bordered
      style="background: linear-gradient(to bottom, #ffffff, #ffffff)">
      <q-list>
        <q-item-label header style="color: #000000">
          Полезные ссылки
        </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <div style="background: linear-gradient(to bottom, #000000, #000000); color: white">
      <q-toolbar>
        <q-toolbar-title header style="font-weight: bold">&nbsp; Coffee | 2023</q-toolbar-title>
      </q-toolbar>
    </div>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Instagram',
    icon: 'photo_camera',
    caption: 'Ещё больше фото здесь',
    link: 'https://instagram.com'
  },
  {
    title: 'Twitter',
    caption: 'Наш аккаунт в Twitter',
    icon: 'rss_feed',
    link: 'https://x.com'
  },
  {
    title: 'Facebook',
    caption: 'Мы в Facebook',
    icon: 'public',
    link: 'https://facebook.com'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup() {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
