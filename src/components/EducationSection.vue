<script setup>
import 'swiper/css';

import { Swiper, SwiperSlide } from 'swiper/vue';
import { Pagination } from "swiper/modules";

const images = [
  {
    src: './favicon.ico',
    alt: 'Sutomo 1 Medan',
  },
  {
    src: './uoft-logo.svg',
    alt: 'University of Toronto',
  },
];

const modules = [Pagination];
const pagination = {
  el: ".education-swiper-pagination",
  clickable: true,
  renderBullet: function (index, className) {
    return `<li class="avatar ${className}" data-slide="${index}" @click="handleSlideClick(${index})">
              <div class="w-24 rounded">
                <img :src="${images[index].src}" :alt="${images[index].alt}" />
              </div>
            </li>`;
  },
};




</script>

<template>
  <div class="hero min-h-screen">
    <div class="hero-content flex-col lg:flex-row">
      <div class="relative w-full">
        <swiper
          :slidesPerView="1"
          :pagination="pagination"
          :modules="modules"
          :initial-slide="1"
          class="educationSwiper text-center"
        >
          <swiper-slide>
            Sutomo 1 Medan
          </swiper-slide>
          <swiper-slide>
            University of Toronto
          </swiper-slide>
        </swiper>
        <ul class="education-swiper-pagination absolute right-0">
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>