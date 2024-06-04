<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p class="text-red-500">And me, hello</p>
    <el-switch v-model="value1" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
const value1 = ref(true)
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
