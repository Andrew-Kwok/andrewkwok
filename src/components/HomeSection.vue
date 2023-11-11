<script setup lang="ts">

import { ref, onMounted } from "vue";
import { emitter } from "@/services/EventBus";

const navbarHeight = ref(0);

onMounted(() => {
  emitter.on('navbar-height', (height: any) => {
    navbarHeight.value = height;
  });
});

</script>

<template>
  <div id="home" :style="`height: calc(100vh - ${navbarHeight}px)`" class="flex justify-center items-center">
    <h1> Hey, I'm </h1> <br />
    <h1> Andrew </h1>
  </div>
</template>

<style scoped>

</style>