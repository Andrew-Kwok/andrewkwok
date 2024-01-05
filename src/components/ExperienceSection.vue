<script setup>

import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectFade } from 'swiper/modules';
import ExperienceCard from "@/components/ExperienceCard.vue";

import 'swiper/css';
import 'swiper/css/effect-flip';
import 'swiper/css/effect-fade';

const sections = ['Work Experience', 'Projects', 'Organization & Volunteer', 'Skills']

const swiperModules = [EffectFade];
const swiperChildModules = [];

const experienceSwiper = ref();

const onExperienceSwiper = (swiper) => {
  experienceSwiper.value = swiper;
};

const slideToIndex = (index) =>   {
  experienceSwiper.value.slideTo(index);
};

const getActiveIndex = () => {
  return experienceSwiper.value?.activeIndex;
};
</script>

<template>
  <div id="experience" class="hero min-h-screen relative">
    <h1 class="absolute bottom-8 left-8 tracking-widest text-2xl font-mono writing-mode-vertical text-mixed border-base-content border-t-8 pt-4">EXPERIENCE</h1>
    <div class="hero-content max-w-md sm:max-w-screen-sm  md:max-w-screen-md lg:max-w-screen-lg xl:max-w-screen-xl relative flex-col lg:flex-row">
      <div class="relative w-full m-4 p-4">

        <ul class="flex justify-end menu menu-horizontal px-1">
          <li
            v-for="(section, index) in sections"
            :key="index"
            @click="slideToIndex(index)"
            class="btn btn-ghost rounded-none px-8 border-base-content border-x-0 border-y-0"
            :class="{ 'border-l-[1px]': index === 0, 'btn-active' : index === getActiveIndex(), 'border-r-[1px]' : index + 1 !== getActiveIndex() }"
          >
            {{ section }}
          </li>
        </ul>

        <swiper
          @swiper="onExperienceSwiper"
          :spaceBetween="30"
          :effect="'fade'"
          :fadeEffect="{
            crossFade: true,
          }"
          :slidesPerView="1"
          :initial-slide="0"
          :navigation="true"
          :allow-touch-move="false"
          :modules="swiperModules"
        >
          <swiper-slide>
            <div class="w-full flex flex-col justify-center">
              <ExperienceCard />
            </div>
          </swiper-slide>
          <swiper-slide>
            <p> Projects </p>
          </swiper-slide>
          <swiper-slide>
            <p> Organization & Volunteer </p>
          </swiper-slide>
          <swiper-slide>
            <p> Skills </p>
          </swiper-slide>
        </swiper>
      </div>
    </div>
  </div>

</template>

<style scoped>

</style>