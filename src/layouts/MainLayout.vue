<template>
  <q-layout view="lHh Lpr lFf" style="background-color: #FFFFFF">
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
      style="background: linear-gradient(to bottom, #3eff88, #8ef9b7)">
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
        <q-toolbar-title header style="font-weight: bold">
          &nbsp; &nbsp; EcoShop | 2023 | Abay Ave 2 &nbsp;
          <a href="/" style="color: #000000"><q-icon name="ion-logo-whatsapp" color="white"
              size="md"></q-icon>&nbsp;&nbsp;&nbsp;</a>
          <a href="/" style="color: #000000"><q-icon name="ion-logo-twitter" color="white"
              size="md"></q-icon>&nbsp;&nbsp;&nbsp;</a>
          <a href="/" style="color: #000000"><q-icon name="ion-logo-instagram" color="white" size="md"></q-icon></a>
        </q-toolbar-title>
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
    icon: 'ion-logo-instagram',
    caption: 'Ещё больше фото здесь',
    link: 'https://instagram.com'
  },
  {
    title: 'Twitter',
    caption: 'Наш аккаунт в Twitter',
    icon: 'ion-logo-twitter',
    link: 'https://x.com'
  },
  {
    title: 'WhatsApp',
    caption: 'Мы в WhatsApp',
    icon: 'ion-logo-whatsapp',
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
