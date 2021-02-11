<template>
  <a href="https://github.com/hasinhayder/vue3-icon-picker" target="_blank"><img alt="Vue logo" src="./assets/logo.png" /></a>
  <icon-picker v-model="icon"/>
  <icon-picker v-model="anotherIcon"/>
  <p>
    
  Icon 1 = {{icon}}<br/>
  Icon 2 = {{anotherIcon}}<br/>

  </p>

  <p>Github: <a href="https://github.com/hasinhayder/vue3-icon-picker" target="_blank">Vue3 Icon Picker</a></p>
</template>

<script>
import {ref} from 'vue'
import IconPicker from './components/IconPicker.vue'
export default {
  components:{
    IconPicker
  },
  setup(){
    const icon = ref('fas fa-circle')
    const anotherIcon = ref('fas fa-far fa-arrow-alt-circle-up')
    return {icon, anotherIcon}
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>