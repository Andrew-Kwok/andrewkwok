<script setup>
import ArrowDown from "@/components/ScrollAnimation/ArrowDown.vue";
// import MouseWheelDown from "@/components/ScrollAnimation/MouseWheelDown.vue";

let props = defineProps(['theme']);
</script>

<template>
  <div class="h-screen relative flex flex-col justify-center items-center">
    <div class="text-left">
      <h1 class="text-7xl"> Hey! I'm </h1>
      <h1 class="text-8xl font-bold"> Andrew </h1>
    </div>

<!--    <MouseWheelDown />-->
    <ArrowDown :theme="props.theme" :isHome="true" />
  </div>
</template>

<style>

</style>