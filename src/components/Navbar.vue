<template>
  <nav class="bg-dark-700 fixed w-full h-8 text-center flex justify-center items-center a">
    <router-link to="/" class="m-2">
      Home
    </router-link>
    <router-link to="/favourite" class="m-2">
      Favourite
    </router-link>

    <button class="icon-btn !outline-none absolute right-3" @click="toggleDark()">
      <div v-if="isDark" i-carbon-moon />
      <div v-else i-carbon-sun />
    </button>
  </nav>
</template>

<script setup lang="ts">
import { isDark, toggleDark } from '~/composables'
</script>

<style scoped>

</style>
