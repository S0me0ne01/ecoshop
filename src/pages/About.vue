<template>
  <q-page :class="theme">

    <div class="article-content">

      <div class="image-container">
        <img src="/images/shop1.jpg" class="rounded-image" />
      </div>

      <div class="article-text">
        <h1 style="margin-top: 10px">{{ $t("about.title") }}</h1>
        <p style="font-size: 30px">{{ $t("about.text") }}</p>
      </div>

    </div>

  </q-page>
</template>

<script>
import { defineComponent, ref, computed } from 'vue'
import { useQuasar } from 'quasar'

import { useBaseStore } from "src/stores/base-store.js";
const baseStore = useBaseStore();

export default defineComponent({
  name: 'About',

  setup() {
    const $q = useQuasar()
    const theme = computed(() => baseStore.getTheme)

    return {
      theme,
    }
  }
})
</script>

<style scoped>
.light {
  background-color: #FFFFFF;
  color: #000000;
}

.dark {
  background-color: #000000;
  color: #FFFFFF;
}
.article-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  margin-top: 30px;
}

.image-container {
  max-width: 600px;
  margin-bottom: 20px;
}

.rounded-image {
  border-radius: 10px;
  max-width: 100%;
  height: auto;
}

.article-text {
  max-width: 800px;
}
</style>
