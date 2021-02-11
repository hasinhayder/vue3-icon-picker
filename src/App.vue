<template>
  <a href="https://github.com/hasinhayder/vue3-icon-picker" target="_blank">
    <img alt="Vue logo" src="./assets/logo.png" />
  </a>

  <div>
    <h1>Click on the icon to see Vue3 Icon Picker in action</h1>
  </div>
  <vue3-icon-picker v-model="icon1" class="icon" />
  <div>
    <h1>Works in inline <vue3-icon-picker v-model="icon2" /> text tooooo</h1>
  </div>
  <div>
    <p>
      And even in paragraphs, like <vue3-icon-picker v-model="icon3" /> this icon
    </p>
  </div>
  <div>
    <h1>
      You can pass <vue3-icon-picker v-model="icon4" style="color:orange" /> inline
      css and attributes as well
    </h1>
  </div>

  <p>
    Icon 1 = {{ icon1 }}<br />
    Icon 2 = {{ icon2 }}<br />
    Icon 3 = {{ icon3 }}<br />
    Icon 4 = {{ icon4 }}<br />
  </p>

  
</template>

<script>
import { ref } from 'vue'
import Vue3IconPicker from './components/Vue3IconPicker.vue'
export default {
  components: {
    Vue3IconPicker
  },
  setup () {
    const icon1 = ref('far fa-grin-hearts')
    const icon2 = ref('far fa-thumbs-up')
    const icon3 = ref('fab fa-github')
    const icon4 = ref('fas fa-code')
    return { icon1, icon2, icon3, icon4 }
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

.icon {
  font-size: 40px;
}
</style>
