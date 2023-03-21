<script setup>
import HelloWorld from './components/HelloWorld.vue'

// Registra a diretiva personalizada global chamada `v-focus`
Vue.directive('focus', {
  // Quando o elemento vinculado é inserido no DOM...
  inserted: function (el) {
    // Coloque o foco no elemento
    el.focus()
  }
})

new Vue({
  directives: {
  focus
  }
})

</script>

<template>
  <div>
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <HelloWorld msg="Vite + Vue" />
  <input v-focus>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
