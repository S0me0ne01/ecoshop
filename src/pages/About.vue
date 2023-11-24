<template>
  <q-page style="background-color: hsl(0, 0%, 100%)">

    <div class="article-content">

      <div class="image-container">
        <img src="/images/shop1.jpg" class="rounded-image" />
      </div>

      <div class="article-text">
        <h1 style="margin-top: 10px">С заботой о клиентах и экологии</h1>
        <p style="font-size: 30px">С самого открытия в далеком 2022 году мы всегда стремились предоставить нашим клиентам
          лучшее качество услуг, не нанося вред природе. Вы можете убедиться в этом сами!</p>
      </div>

    </div>

  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useQuasar } from 'quasar'

export default defineComponent({
  name: 'About',

  setup() {
    const $q = useQuasar()

    return {

    }
  }
})
</script>

<style scoped>
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
