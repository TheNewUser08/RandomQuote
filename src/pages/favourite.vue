<template>
  <div v-if="favQuotes" class="grid grid-cols-4 gap-4 ">
    <div v-for="quote in favQuotes" :key="quote._id">
      <div class="h-full bg-gray-800 rounded-lg p-10 pb-0 flex ">
        <div v-if="quote" class="flex flex-col justify-around">
          <h3 class="relative bottom-3 text-3xl font-bold text-indigo-400">
            {{ quote?.author }}
          </h3>
          <p class="text-2xl ">
            "{{ quote?.content }}"
          </p>

          <div>
            <button class="i-bi:x-lg" />
          </div>
        </div>
        <div v-else class=" bg-gray-800 rounded-lg p-10 pb-0 ">
          loading...
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import type { Ref } from 'vue'
import { ref } from 'vue'
import type { quoteRes } from '~/composables'

const favQuotes: Ref<quoteRes[]> = ref(JSON.parse(localStorage.getItem('quotes')))


</script>

<style scoped>

</style>
