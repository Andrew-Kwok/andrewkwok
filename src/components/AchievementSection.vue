<script setup>

const achievements = [
  {
    "id": 1,
    "title": "International Olympiad in Informatics 2022",
    "award": "Bronze Medal",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.",
    "color": "blue",
    "icon": "mdi-trophy"
  },
  {
    "id": 2,
    "title": "Indonesia's National Olympiad in Informatics (KSN)  2020",
    "award": "Gold Medal",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.",
    "color": "red",
    "icon": "mdi-trophy"
  }
]

import 'swiper/css';

import { Swiper, SwiperSlide } from 'swiper/vue';
import { Pagination } from "swiper/modules";

const swiperModules = [Pagination];

</script>

<template>
  <div id="achievement" class="min-h-screen flex justify-center items-center bg-base-200">
    <div class="relative max-w-6xl h-64 bg-pink">
      <div class="absolute inline-block top-0 left-0 h-8 z-10">
        <h1> Achievements </h1>
      </div>
      <swiper
        :spaceBetween="30"
        :pagination="{
        clickable: true,
      }"
        :modules="swiperModules"
        class="achievement-swiper bg-cyan-500"
      >
        <swiper-slide class="h-screen">Slide 1</swiper-slide>
        <swiper-slide>Slide 2</swiper-slide>
        <swiper-slide>Slide 3</swiper-slide>
      </swiper>
  </div>
  </div>

</template>

<style>

.swiper {
  width: 100%;
  height: 100%;
}

</style>