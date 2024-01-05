<script setup>
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

console.log(props.award === undefined);

</script>


<template>
  <div class="p-2 flex w-[26rem]">
    <figure class="flex justify-center">
      <img class="h-[30px] object-cover" v-if="medal === 'gold'" src="gold-medal.png" alt="Gold Medal">
      <img class="h-[30px] object-cover" v-else-if="medal === 'silver'" src="silver-medal.png" alt="Silver Medal">
      <img class="h-[30px] object-cover" v-else-if="medal === 'bronze'" src="bronze-medal.png" alt="Bronze Medal">
      <img class="h-[30px] object-cover" v-else src="other-medal.png" alt="Other Medal">
    </figure>
    <div class="ml-1 w-full">
      <h1 class="font-bold"> {{competition}} </h1>
      <div class="flex justify-between">
        <h2 v-if="award !== null && award !== undefined && award !== ''"> {{award}}, {{host}} </h2>
        <h2 v-else> {{host}} </h2>
        <p class="font-italic"> {{date}} </p>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>