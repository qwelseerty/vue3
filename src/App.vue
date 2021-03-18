<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Today is {{ now }}</h2>
      <span>Opens: <strong>{{ openRate }}</strong> | Reads : <strong>{{ readRate }}</strong> </span>
    </div>

    <app-news
        v-for="item in news"
        :title="item.title"
        :key="item.id"
        :id="item.id"
        :is-open="item.isOpen"
        :was-read="item.wasRead"
        @open-news="openNews"
        @read-news="readNews"
        @unmark="unreadNews"
    ></app-news>

  </div>

</template>

<script>
import AppNews from "@/components/AppNews";

export default {
  data() {
    return {
      openRate: 0,
      readRate: 0,
      now: new Date().toLocaleDateString(),
      news: [{
        title: 'first',
        id: 1,
        isOpen: false,
        wasRead: false
      },
        {
          title: 'second',
          id: 2,
          isOpen: false,
          wasRead: false
        }
      ]
    }
  },
  provide(){
    return {
      title:'123',
      news:this.news
    }
  },
  components: {
    'app-news': AppNews
  },
  methods: {
    openNews() {
      this.openRate++
    },
    readNews(id) {
      const idx = this.news.findIndex(news => news.id === id)
      this.news[idx].wasRead = true
      this.readRate++
    },
    unreadNews(id){
      const news = this.news.find(news=>news.id===id)
      news.wasRead = false
      this.readRate--
    }
  }
}
</script>

<style scoped>
  h2 {
    color: darkcyan;
  }
</style>