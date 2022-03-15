<template>
  <div v-if="quote" class="w-1/3 bg-gray-800 rounded-lg px-10  min-h-90 grid grid-rows-3 grid-cols-1">
    <h3 class="text-3xl font-bold text-indigo-400 flex justify-center items-center">
      {{ quote?.author }}
    </h3>
    <p class="text-2xl flex justify-center items-center">
      "{{ quote?.content }}"
    </p>
    <div class="flex flex-col justify-end">
      <div class="h-0.25 bg-white" />
      <div>
        <button i-carbon:arrow-right class="mt-2 text-lg" @click="getQuote" />
        <button i-ph-heart-straight-fill class="mt-2 text-lg" @click="addQuote" />
      </div>
    </div>
  </div>
  <div v-else class="w-1/3 bg-gray-800 rounded-lg p-10 pb-0 min-h-100">
    loading...
  </div>
</template>

<script setup lang="ts">

import type { Ref } from 'vue'
import { onBeforeMount, ref } from 'vue'
import type { quoteRes } from '~/composables'

const quote: Ref<quoteRes|null> = ref(null)

const getQuote = async() => {
  const res = await fetch('https://api.quotable.io/random')
  quote.value = await res.json()
}

const addQuote = async() => {
  if (localStorage.getItem('quotes') === null) {
    localStorage.setItem('quotes', JSON.stringify([quote.value]))
  }
  else {
    const favQuotes = JSON.parse(localStorage.getItem('quotes'))
    favQuotes.push(quote.value)
    localStorage.setItem('quotes', JSON.stringify(favQuotes))
  }
}

onBeforeMount(async() => {
  await getQuote()
})
</script>

<style scoped>

</style>
