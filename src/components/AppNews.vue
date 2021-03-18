<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <button class="btn" @click="openz">{{ isNewsOpen ? 'Close' : 'Open' }}</button>
    <button v-if="wasRead" class="btn danger" @click="$emit('unmark',id)">doesen't read</button>
    <div v-if="isNewsOpen">
      <hr/>
      <p>Lorem ipsum dolor sit amet.</p>
      <button v-if="!wasRead" class="btn primary" @click="mark">Read this news</button>
    </div>
  </div>
</template>

<script>
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

  }
}
</script>

<style scoped>

</style>