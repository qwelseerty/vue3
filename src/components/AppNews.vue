<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <button class="btn" @click="openz">{{isNewsOpen?'Close':'Open'}}</button>
    <p v-if="isNewsOpen ">Lorem ipsum dolor sit amet.</p>
  </div>
</template>

<script>
export default {
  props: {
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
        this.$emit('open-news',42)
      }
    }
  }
}
</script>

<style scoped>

</style>