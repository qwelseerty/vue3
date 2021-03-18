<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <app-button @action="openz"> {{isNewsOpen ? 'Close' : 'Open'}}</app-button>
    <app-button v-if="wasRead"
                color="danger" @action="$emit('unmark',id)"
    >doesen't read
    </app-button>
    <div v-if="isNewsOpen">
      <hr/>
      <p>Lorem ipsum dolor sit amet.</p>
      <app-button v-if="!wasRead"
                  color="primary"
                  @action="mark"
      >Read this news
      </app-button>
      <app-news-list></app-news-list>
    </div>
  </div>
</template>

<script>
import AppButton from "@/components/AppButton";
import AppNewsList from "@/components/AppNewsList";

export default {
  emits: {
    'open-news': null,
    ' read-news'(id) {
      if (id) {
        return true
      }
      console.warn('doesent have id')
      return false
    }, unmark: null
  },

  props: {
    wasRead: Boolean,
    title: {
      type: String,
      required: true
    },
    id: {
      type: Number,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: false,
      default: false,
      validator(value) {
        return value === true || value === false
      }
    }
  },
  data() {
    return {
      isNewsOpen: this.isOpen
      // isOpen: false
    }
  },
  methods: {
    openz() {
      this.isNewsOpen = !this.isNewsOpen
      if (this.isNewsOpen) {
        this.$emit('open-news', 42)
      }
    },
    mark() {
      this.isNewsOpen = false
      this.$emit('read-news', this.id)
    },
    // unmark() {
    //   this.$emit('unmark', this.id)
    // }

  },
  components: {
    AppButton,
    AppNewsList
  }
}
</script>

<style scoped>

</style>