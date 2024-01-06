<script setup>
import ArrowDown from "@/components/ScrollAnimation/ArrowDown.vue";

const props = defineProps({
  theme: String,
});
</script>

<template>
  <div id="contact" class="h-screen flex flex-col justify-center items-center text-center">
    <h1 class="absolute bottom-8 left-8 tracking-widest text-2xl font-mono writing-mode-vertical text-mixed border-base-content border-t-8 pt-4">CONTACT</h1>

    <h1 class="text-7xl"> Reach Me Out! </h1>

    <ul class="flex flex-row justify-around w-2/5 list-none text-8xl mt-5 contact-list">
      <li> <a href="mailto:andrew.andrew@mail.utoronto.ca"> <font-awesome-icon icon="fas fa-envelope" class="contact-list-icon" id="contact-email" /> </a> </li>
      <li> <a href="https://github.com/Andrew-Kwok"> <font-awesome-icon icon="fab fa-github" class="contact-list-icon" id="contact-git" /> </a> </li>
      <li> <a href="https://www.instagram.com/andrewkwok__/"> <font-awesome-icon icon="fab fa-instagram" class="contact-list-icon" id="contact-ig" /> </a> </li>
      <li> <a href="https://www.linkedin.com/in/andrew-kwok-33a6b7184/"> <font-awesome-icon icon="fab fa-linkedin" class="contact-list-icon" id="contact-li" /> </a> </li>
      <li> <a href="https://wa.me/qr/VLKIV2QJQUM4E1"> <font-awesome-icon icon="fab fa-whatsapp" class="contact-list-icon" id="contact-wa" /> </a> </li>
    </ul>

    <p class="absolute bottom-2 text-base-300 font-italic" style="font-family: 'Futura CondensedLight'"> Hope for the best, prepare for the worst. </p>
  </div>
</template>

<style scoped>

</style>