<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from 'swiper/vue';
import { FreeMode, Scrollbar, Mousewheel } from "swiper/modules";

import AchievementCard from "@/components/AchievementCard.vue";

import 'swiper/css';
import 'swiper/css/free-mode';
import 'swiper/css/scrollbar';

const years = Array.from({ length: 6 }, (_, index) => 2023 - index);
const modules = [FreeMode, Scrollbar, Mousewheel];

const yearSwiper = ref();
const onYearSwiper = (swiper) => {
  yearSwiper.value = swiper;
};

const achievementSwiper = ref();
const onAchievementSwiper = (swiper) => {
  achievementSwiper.value = swiper;
};

const achievementSlideToIndex = (index) =>   {
  achievementSwiper.value.slideTo(index);
};

const achievementSlideToYear = (year) =>   {
  achievementSwiper.value.slideTo(2023 - year);
};

const achievementGetActiveYear = () => {
  return 2023 - achievementSwiper.value?.activeIndex;
};

</script>

<template>
  <div id="achievement" class="hero min-h-screen relative">
    <h1 class="absolute bottom-8 left-8 tracking-widest text-2xl font-mono writing-mode-vertical text-mixed border-base-content border-t-8 pt-4">ACHIEVEMENTS</h1>
    <div class="hero-content max-w-md sm:max-w-screen-sm md:max-w-screen-md lg:max-w-screen-lg">
      <div class="w-full m-4 p-4">
        <div class="flex">
          <div class="w-4/5">
            <swiper
              @swiper="onYearSwiper"
              :spaceBetween="30"
              :slidesPerView="'auto'"
              :freeMode="true"
              :mousewheel="true"
              :modules="modules"
            >
              <swiper-slide v-for="year in years" :key="year" class="max-w-[3rem]" @click="achievementSlideToYear(year)">
                <p class="text-center hover:cursor-pointer" :class="{ 'border-primary border-b-2' : achievementGetActiveYear  () === year }"> {{ year }} </p>
              </swiper-slide>
            </swiper>
          </div>

          <div class="join">
            <button class="join-item btn">«</button>
            <button class="join-item btn">»</button>
          </div>
        </div>

        <swiper
          @swiper="onAchievementSwiper"
          :spaceBetween="100"
          :slidesPerView="'auto'"
          :freeMode="true"
          :scrollbar="{ draggable: true }"
          :mousewheel="true"
          :modules="modules"
        >
          <swiper-slide class="max-w-fit">
            <div class="grid gap-4 grid-rows-4 grid-flow-col overflow-auto">
              <AchievementCard
                :competition="'2023 Dean\'s List Scholar'"
                :medal="'other'"
                :host="'University of Toronto'"
                :date="'Jun. 2023'"
              />
            </div>
          </swiper-slide>
          <swiper-slide class="max-w-fit">
            <div class="grid gap-4 grid-rows-4 grid-flow-col overflow-auto">
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2022'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2022'"
              />
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2022'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2022'"
              />
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2022'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2022'"
              />
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2022'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2022'"
              />
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2022'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2022'"
              />
            </div>
          </swiper-slide>
          <swiper-slide class="max-w-fit">
            <div class="grid gap-4 grid-rows-4 grid-flow-col overflow-auto">
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2021'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2021'"
              />
            </div>
          </swiper-slide>
          <swiper-slide class="max-w-fit">
            <AchievementCard
              :competition="'National Olympiad in Informatics (KSN) 2020'"
              :award="'Gold Medal'"
              :medal="'gold'"
              :host="'Indonesia'"
              :date="'Oct. 2020'"
            />

          </swiper-slide>
          <swiper-slide class="max-w-fit">
            <div class="grid gap-4 grid-rows-4 grid-flow-col overflow-auto">
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2019'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2019'"
              />
            </div>
          </swiper-slide>
          <swiper-slide class="max-w-fit">
            <div class="grid gap-4 grid-rows-4 grid-flow-col overflow-auto">
              <AchievementCard
                :competition="'International Olympiad in Informatics (IOI) 2018'"
                :award="'Bronze Medal'"
                :medal="'bronze'"
                :host="'IOI Indonesia'"
                :date="'Oct. 2018'"
              />
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </div>
  </div>

</template>

<style>
</style>