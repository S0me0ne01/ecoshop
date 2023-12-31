<template>
  <q-layout view="lHh Lpr lFf" :class="theme">
    <!-- HEADER -->
    <q-header elevated>
      <q-toolbar style="background-color: #4cff91">
        <q-btn flat dense round icon="menu" aria-label="Menu" style="color: #000000" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          &nbsp;&nbsp;<a href="/"><img src="/images/logo.png" height="50" style="padding-top: 8px" /></a>
        </q-toolbar-title>

        <q-toolbar-title style="text-align: end; padding-right: 20px">
          <q-btn @click="setTheme()" flat>
            <q-icon v-if="theme == 'light'" name="light_mode" color="black" />
            <q-icon v-else name="nightlight_round" color="black" />
          </q-btn>

          <q-btn flat>

            <q-list style="width: 80px">
              <q-select :dark="theme == 'dark'" v-model="locale" :options="localeOptions" dense borderless emit-value map-options
                options-dense style="padding: 10px">
              </q-select>
            </q-list>

          </q-btn>
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-not-above bordered
      style="background: linear-gradient(to bottom, #3eff88, #8ef9b7)">
      <q-list>
        <q-item-label header style="color: #000000">
          {{ $t('drawer.title') }}
        </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <div>
      <q-toolbar :class="theme">
        <q-toolbar-title header style="font-weight: bold; font-size: 15px">
          &nbsp; &nbsp; EcoShop &nbsp; 2023 &nbsp; Abay Ave 2 &nbsp;
          <a href="/" style="color: #4cff91"><q-icon name="ion-logo-whatsapp"
              size="sm"></q-icon></a>&nbsp;&nbsp;&nbsp;
          <a href="/" style="color: #4cff91"><q-icon name="ion-logo-twitter"
              size="sm"></q-icon></a>&nbsp;&nbsp;&nbsp;
          <a href="/" style="color: #4cff91"><q-icon name="ion-logo-instagram" size="sm"></q-icon></a>
        </q-toolbar-title>
      </q-toolbar>
    </div>
  </q-layout>
</template>

<script>
import { defineComponent, ref, computed } from 'vue'
import { useI18n } from 'vue-i18n'
import EssentialLink from 'components/EssentialLink.vue'

import { useBaseStore } from "src/stores/base-store.js";
const baseStore = useBaseStore();

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup() {
    const { locale } = useI18n({ useScope: 'global' })
    const t = useI18n({ useScope: 'global' })
    const leftDrawerOpen = ref(false)
    const theme = computed(() => baseStore.getTheme)

    const linksList = [
      {
        title: 'Instagram',
        icon: 'ion-logo-instagram',
        link: 'https://instagram.com'
      },
      {
        title: 'Twitter',
        icon: 'ion-logo-twitter',
        link: 'https://x.com'
      },
      {
        title: 'WhatsApp',
        icon: 'ion-logo-whatsapp',
        link: 'https://facebook.com'
      }
    ]

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      locale,
      localeOptions: [
        { value: 'kz', label: 'KZ' },
        { value: 'ru', label: 'RU' },
        { value: 'en-US', label: 'EN' },
      ],
      theme
    }
  },

  methods: {
    async setTheme() {
      await baseStore.setTheme();
    }
  }
})
</script>

<style>
light {
  background-color: #FFFFFF;
  color: #000000;
}

.dark {
  background-color: #000000;
  color: #FFFFFF;
}
</style>
