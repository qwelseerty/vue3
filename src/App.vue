<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Today is {{ now }}</h2>
    </div>

    <app-news
        v-for="item in news"
        :title="item.title"
        :key="item.id"
        :id="item.id"
        :is-open="item.isOpen"
    ></app-news>

  </div>

</template>

<script>
import AppNews from "@/components/AppNews";

export default {
  data() {
    return {
      now: new Date().toLocaleDateString(),
      news: [{
        title: 'first',
        id: 1,
        isOpen:false
      },
        {
          title: 'second',
          id: 2,
          isOpen:false
        }
      ]
    }
  },
  components: {
    'app-news': AppNews
  }
}
</script>

<style scoped>

</style>