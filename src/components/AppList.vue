<template>
  <div class="card">
    <ul>
      <li v-for="(item,idx) in 5" :key="item" >
        <slot :iter="item"
              :idx="idx"
        />
      </li>
    </ul>

  </div>
</template>

<script>
export default {}
</script>

<style scoped>

</style>