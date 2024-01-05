<script setup>
import 'swiper/css';

import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Pagination } from "swiper/modules";

const images = [
  {
    src: '/sutomo-logo.png',
    alt: 'Sutomo 1 Medan',
  },
  {
    src: './uoft-logo.svg',
    alt: 'University of Toronto',
  },
];

const modules = [Autoplay, Pagination];
const pagination = {
  el: ".about-me-swiper-pagination",
  clickable: true,
  renderBullet: function (index, className) {
    return `<li class="avatar ${className}" data-slide="${index}" @click="handleSlideClick(${index})">
              <div class="m-2 w-16 h-16 btn p-0">
                <img src="${images[index].src}" alt="${images[index].alt}" />
              </div>
            </li>`
  },
};


</script>

<template>
  <div class="hero min-h-screen relative">
    <h1 class="absolute bottom-8 left-8 tracking-widest text-2xl font-mono writing-mode-vertical text-mixed border-base-content border-t-8 pt-4">ABOUT ME</h1>
    <div class="hero-content max-w-md sm:max-w-screen-sm  md:max-w-screen-md lg:max-w-screen-lg xl:max-w-screen-xl relative flex-col lg:flex-row">

      <div class="w-full lg:w-1/2 min-h-fit m-4">
        <div class="collapse collapse-arrow bg-base-200 m-4 my-8">
          <input type="radio" name="my-accordion-2" checked="checked" />
          <div class="collapse-title text-xl font-medium">
            Computer Science Undergraduate
          </div>
          <div class="collapse-content">
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.
            </p>
          </div>
        </div>
        <div class="collapse collapse-arrow bg-base-200 m-4 my-8">
          <input type="radio" name="my-accordion-2" />
          <div class="collapse-title text-xl font-medium">
            Software Engineer
          </div>
          <div class="collapse-content">
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.
            </p>
          </div>
        </div>
        <div class="collapse collapse-arrow bg-base-200 m-4 my-8">
          <input type="radio" name="my-accordion-2" />
          <div class="collapse-title text-xl font-medium">
            Competitive Programmer
          </div>
          <div class="collapse-content">
            <p>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.
            </p>
          </div>
        </div>
      </div>

      <div class="relative w-full lg:w-1/2 m-4 p-4">
        <swiper
          :slidesPerView="1"
          :pagination="pagination"
          :modules="modules"
          :initial-slide="1"
          :autoplay="{
            delay: 2500,
            disableOnInteraction: true,
          }"
          :navigation="true"
          class="aboutMeSwiper"
        >
          <swiper-slide>
            <div class="">
              <h1 class="text-4xl font-bold"> Sutomo 1 Medan </h1>
              <p> 2010 - 2022 </p>
              <div class="divider"></div>
              <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.
              </p>
            </div>
          </swiper-slide>
          <swiper-slide>
            <div class="">
              <h1 class="text-4xl font-bold"> University of Toronto </h1>
              <p> 2022 - present </p>
              <div class="divider"></div>
              <p>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec auctor, nisl eu ultricies fermentum, nunc libero ultricies urna, eget ultricies velit nisl eu nunc. Sed vitae nisl eget nunc aliquam aliquet. Sed vitae nisl eget nunc aliquam aliquet.
              </p>
            </div>
          </swiper-slide>
        </swiper>
        <ul class="about-me-swiper-pagination absolute right-0">
        </ul>
      </div>
    </div>
  </div>
</template>

<style scoped>
.writing-mode-vertical {
  writing-mode: vertical-rl;
}

.text-mixed {
  text-orientation: mixed;
}
</style>