<script setup lang="ts">
import { ref, computed} from 'vue'
import PlayPage from "./pages/PlayPage.vue";
import TopPage from "./pages/TopPage.vue";
import NotFound from "./pages/NotFound.vue"

const routes = {
  '/': TopPage,
  '/play': PlayPage,
  '/non-existent-path': NotFound
}
const currentPath = ref(window.location.hash);

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})
const currentView = computed(() => {
  // 取得したurlの#以降のhash値から#を取り除くためにsplice(1)をしている
  return routes[currentPath.value.slice(1) || '/'] || NotFound
})
  </script>

<template>
  <header>
    <a href="#/">TopPage</a> |
    <a href="#/play">PlayPage</a> |
    <a href="#/non-existent-path">Broken Link</a>
  </header>
  <component :is="currentView" />
</template>

<style scoped>

</style>
