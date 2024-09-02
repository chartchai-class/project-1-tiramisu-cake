<script setup lang="ts">
import { toRefs, defineProps } from 'vue'
import type { Country } from '@/types'

const props = defineProps<{
  country: Country
}>()
const { country } = toRefs(props)
</script>

<template>
  <div class="flex">
    <!-- Left Half: Country Flag -->
    <div class="w-1/2 flex justify-center items-center">
      <img :src="country.value.flag" :alt="`${country.value.name} Flag`" class="max-w-full h-auto"/>
    </div>

    <!-- Right Half: Country Information -->
    <div class="w-1/2 p-4">
      <h1 class="text-2xl font-bold">{{ country.value.name }}</h1>
      <p><strong>Capital:</strong> {{ country.value.capital }}</p>
      <p><strong>Language:</strong> {{ country.value.language }}</p>
      <p><strong>Gold Medals:</strong> {{ country.value.gold }}</p>
      <p><strong>Silver Medals:</strong> {{ country.value.silver }}</p>
      <p><strong>Bronze Medals:</strong> {{ country.value.bronze }}</p>

      <h2 class="mt-4 text-xl font-semibold">Top Sports</h2>
      <ul>
        <li v-for="(sport, index) in country.value.sports" :key="index">
          <strong>{{ sport.sport }}:</strong> 
          Gold: {{ sport.medals.gold }}, 
          Silver: {{ sport.medals.silver }}, 
          Bronze: {{ sport.medals.bronze }}
        </li>
      </ul>
    </div>
  </div>
</template>
