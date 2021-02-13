<template>
  <div class="flex items-center justify-center h-full flex-col">

    <!-- Header section -->
    <div class="flex  w-full justify-center py-5">
      <a
        class="flex sm:flex-row flex-col justify-center items-center font-extrabold text-5xl no-underline bg-clip-text text-transparent bg-gradient-to-r from-green-500 to-gray-500"
        href="https://github.com/hasinhayder/vue3-icon-picker"
        target="_blank"
      >
        <img class="w-1/6" alt="Vue logo" :src="images.logo" />
        Vue3 Icon Picker
      </a>
    </div>

    <!-- Preview Image section -->

    <div class="flex justify-center py-2">
      <img class="w-4/6" :src="images.preview" />
    </div>

    <!-- Basic Example -->

    <div class="py-5 my-6 border-1 border-gray-300 px-5 rounded-md shadow-xl bg-white">
      <div
        class="bg-green-500 border-none text-gray-200 text-3xl px-8 py-3 rounded shadow-xl items-center flex gap-3 justify-center"
      >
        Click on the icon to see in action
        <icon-picker v-model="icon1" class="icon" />
      </div>

      <ssh-pre
        class="text-2xl shadow-xl"
        dark="true"
        language="html"
        copy-button
        label="Basic Example"
      >
        <template v-slot:copy-button>
          <i class="far fa-copy"></i>
        </template>
        &lt;icon-picker v-model="icon1" class="icon" /&gt;
      </ssh-pre>
    </div>

  <!-- Inline Example -->

    <div class="py-5  my-6 border-1 border-gray-300 px-5 rounded-md shadow-xl bg-white">
      <div
        class="bg-green-500 border-none text-gray-200 text-2xl px-8 py-3 rounded shadow-xl items-center flex gap-3 justify-center"
      >
      Works in inline <icon-picker v-model="icon2" /> text tooooo
      </div>
      <ssh-pre
        class="text-xl"
        dark="true"
        language="html"
        copy-button
        label="Inline Example"
      >
        <template v-slot:copy-button>
          <i class="far fa-copy"></i>
        </template>
        &lt;h1&gt;Works in inline &lt;con-picker v-model="icon2" /&gt; text
        tooooo&lt;/h1&gt;
      </ssh-pre>
    </div>

    
    <div class="py-5 my-6 border-1 border-gray-300 px-5 rounded-md shadow-xl bg-white">
      <div
        class="bg-green-500 text-2xl border-none text-gray-200  px-8 py-3 rounded shadow-xl items-center flex gap-3 justify-center"
      >
      
        You can pass
        <icon-picker v-model="icon2" style="color: white" /> inline css and
        attributes as well
      
      </div>

      <ssh-pre
        class="text-xl"
        dark="true"
        language="html"
        copy-button
        label="Inline CSS Example"
      >
        <template v-slot:copy-button>
          <i class="far fa-copy"></i>
        </template>
        &lt;con-picker v-model="icon2" style="color: #40b983" /&gt;
      </ssh-pre>
    </div>

    <div class="py-5">
      <p>
        And even in paragraphs, like <icon-picker v-model="icon3" /> this icon
      </p>

     
    </div>

    

    <p>
      <!-- Place this tag where you want the button to render. -->
      <a
        class="github-button"
        href="https://github.com/hasinhayder/vue3-icon-picker"
        data-color-scheme="no-preference: dark; light: light; dark: dark;"
        data-size="large"
        data-show-count="true"
        aria-label="Star ntkme/github-buttons on GitHub"
      >
        Star
      </a>
    </p>
  </div>

</template>

<script>
import { ref } from "vue";
import IconPicker from "./components/IconPicker.vue";
import SshPre from "simple-syntax-highlighter";
import "simple-syntax-highlighter/dist/sshpre.css";
import logo from './assets/logo.png'
import preview from './assets/preview.png'
export default {
  data(){
    return {
      images: {
        logo: logo,
        preview: preview
      }
    }
  },
  components: {
    IconPicker,
    SshPre,
  },
  setup() {
    const icon1 = ref("far fa-grin-hearts");
    const icon2 = ref("far fa-thumbs-up");
    const icon3 = ref("fab fa-github");
    const icon4 = ref("fas fa-code");
    return { icon1, icon2, icon3, icon4 };
  },
};
</script>

<style>
body {
  background: #f1f3f5;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}

.icon {
  font-size: 40px;
}
</style>
