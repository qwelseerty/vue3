<template>
  <div class="container pt-1">
    <div class="card">
      <async></async>
      <h2>dinamic async</h2>

      <app-button
          ref="myBtn"
          :color="oneColor"
          @action="active='one'">one
      </app-button>

      <app-button
          :color="twoColor"
          @action="active='two'">two
      </app-button>
    </div>

    <keep-alive>
      <component :is="componentName"></component>
    </keep-alive>

  </div>
</template>

<script>
import AppButton from "@/components/AppButton";
import AppOne from "@/components/AppOne";
import AppTwo from "@/components/AppTwo";

export default {
  data() {
    return {
      active: 'one'
    }
  },
  mounted() {
    // setTimeout(()=>{
    //   this.componentName = 'new next'
    // },1500)
    console.log(this.$refs.myBtn)
  },

  components: {
    AppButton,
    AppOne,
    AppTwo
  },
  computed: {
    componentName:{
      get(){ return 'app-' + this.active},
      set(value){
        console.log(value)}

    // componentName() {
    //   return 'app-' + this.active
      //   if (this.active === 'one') {
      //     return 'app-one'
      //   }
      //   return 'app-two'
    },
    oneColor(){
      return this.active === 'one'? 'primary' : ''
    },
    twoColor(){
      return  this.active === 'two'? 'primary' : ''
    }
  }
}
</script>

<style scoped>

</style>