<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Today is {{ now }}</h2>
      <span>Opens: {{openRate}}</span>
    </div>

    <app-news
        v-for="item in news"
        :title="item.title"
        :key="item.id"
        :id="item.id"
        :is-open="item.isOpen"
        @open-news = "openNews"
    ></app-news>

  </div>

</template>

<script>
import AppNews from "@/components/AppNews";

export default {
  data() {
    return {
      openRate:0,
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
  },
  methods:{
    openNews(){
      this.openRate++
    }
  }
}
</script>

<style scoped>

</style>