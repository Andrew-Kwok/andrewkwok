<script setup>
import { computed } from "vue";

const props = defineProps({
  competition: String,
  medal: {
    type: String,
    validator: value => ['gold', 'silver', 'bronze', 'other'].includes(value)
  },
  host: String,
  award: String | null,
  date: String,
})

const combinedAwardHost = computed(() => {
  if (props.award !== null && props.award !== undefined && props.award !== '') {
    return `${props.award}, ${props.host}`
  }
  return props.host
})
</script>


<template>
  <div class="p-2 flex w-[26rem]">
    <figure class="flex justify-center">
      <img class="h-[30px] object-cover" v-if="medal === 'gold'" src="medal-gold.png" alt="Gold Medal">
      <img class="h-[30px] object-cover" v-else-if="medal === 'silver'" src="medal-silver.png" alt="Silver Medal">
      <img class="h-[30px] object-cover" v-else-if="medal === 'bronze'" src="medal-bronze.png" alt="Bronze Medal">
      <img class="h-[30px] object-cover" v-else src="medal-other.png" alt="Other Medal">
    </figure>
    <div class="ml-1 w-full">
      <h1 class="font-bold" v-html="competition"> </h1>
      <div class="flex justify-between">
        <h2 v-html="combinedAwardHost"> </h2>
        <p class="font-italic" v-html="date"></p>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>