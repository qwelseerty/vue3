<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <button class="btn" @click="isOpen = !isOpen">open</button>
    <p v-if="isOpen ">Lorem ipsum dolor sit amet.</p>
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
      validator(value){
        return value === true || value === false
      }
    }
  },
  data() {
    return {
      // isOpen: false
    }
  }
}
</script>

<style scoped>

</style>