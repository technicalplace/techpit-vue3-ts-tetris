<script setup lang="ts">
import { Ref, ref } from 'vue'
const name:Ref<string> = ref('');
</script>

<template>
  <h1 style="color: #ccc">トップページ</h1>
  <p v-if="name.length">{{ name }}</p>
  <input
    style="width: 250px"
    type="text"
    v-model="name"
    placeholder="名前を入力してください（10文字以内）"
  ><br>
  <button><a href="#/play">ゲームスタート！</a></button>
</template>

<style scoped>

</style>