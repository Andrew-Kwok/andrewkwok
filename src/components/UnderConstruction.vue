<script setup lang="ts">
  import { ref, onMounted } from "vue";

  const countdown = ref(3);
  onMounted(() => {
    setInterval(() => {
      countdown.value--;
      if (countdown.value <= 0) {
        window.location.href = "https://andrew-kwok.github.io/";
      }
    }, 1000);
  });
</script>

<template>
  <div class="under-construction">
    <h1 class="green">Under Construction</h1>
    <h3>
      This page is under construction. Visit my old website at <a href="https://andrew-kwok.github.io/" target="_blank" rel="noopener">andrew-kwok.github.io</a>.
    </h3>

    <p>Redirecting in {{ countdown }} seconds...</p>
  </div>
</template>

<style scoped>

</style>