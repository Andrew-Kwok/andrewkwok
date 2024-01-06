<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from 'swiper/vue';
import { FreeMode, Scrollbar, Mousewheel } from "swiper/modules";

import AchievementCard from "@/components/AchievementCard.vue";

import 'swiper/css';
import 'swiper/css/free-mode';
import 'swiper/css/scrollbar';
import ArrowDown from "@/components/ScrollAnimation/ArrowDown.vue";

const props = defineProps({
  theme: String,
});

const achievements = [
  {
    year: 2023,
    awards: [
      {
        competition: '2023 Dean\'s List Scholar',
        medal: 'other',
        host: 'University of Toronto',
        date: 'Jun. 2023',
      },
      {
        competition: 'The 2022 ICPC East Central NA Regional Contest',
        award: 'Bronze Medal',
        medal: 'bronze',
        host: 'ICPC',
        date: 'Feb. 2022',
      }
    ]
  },
  {
    year: 2022,
    awards: [
      {
        competition: 'International Olympiad in Informatics (IOI) 2022',
        award: 'Bronze Medal',
        medal: 'bronze',
        host: 'IOI Indonesia',
        date: 'Oct. 2022',
      },
      {
        competition: '9<sup>th</sup> National Programming & Logic Competition',
        award: '1<sup>st</sup> Rank',
        medal: 'gold',
        host: 'Universitas Ciputra',
        date: 'Jan. 2022',
      }
    ],
  },
  {
    year: 2021,
    awards: [
      {
        competition: 'Programming Competition at Information Technology Creative Competition 2021',
        award: '1<sup>st</sup> Rank',
        medal: 'gold',
        host: 'Universitas Udayana',
        date: 'Nov. 2021',
      },
      {
        competition: 'Schematics National Programming Contest Junior',
        award: '2<sup>nd</sup> Rank',
        medal: 'silver',
        host: 'Institut Teknologi Sepuluh November',
        date: 'Oct. 2021',
      },
      {
        competition: 'The 2021 Bina Nusantara Programming Contest for Highschool Student',
        award: 'Bronze Medal',
        medal: 'bronze',
        host: 'Binus University',
        date: 'Oct. 2021',
      },
      {
        competition: 'Junior Competitive Programming Contest at COMPFEST 13',
        award: 'Honorable Mention',
        medal: 'other',
        host: 'Universitas Indonesia',
        date: 'Oct. 2021',
      },
      {
        competition: 'Mikroskil Ideafuse Competitive Programming Competition 2021 for Highschool Students',
        award: '1<sup>st</sup> Rank',
        medal: 'gold',
        host: 'Universitas Mikroskil',
        date: 'Sep. 2021',
      },
      {
        competition: 'Sutomo 1 Senior High School Programming Competition 2021',
        award: '1<sup>st</sup> Rank',
        medal: 'gold',
        host: 'SMA Sutomo 1 Medan',
        date: 'Feb. 2021',
      },
      {
        competition: 'Informatics Logical Programming Competition',
        award: '3<sup>rd</sup> Rank',
        medal: 'bronze',
        host: 'Universitas Surabaya (UBAYA)',
        date: 'Jan. 2021',
      }
    ]
  },
  {
    year: 2020,
    awards: [
      {
        competition: 'National Olympiad in Informatics (KSN) 2020',
        award: 'Gold Medal',
        medal: 'gold',
        host: 'Indonesia',
        date: 'Oct. 2020',
      },
      {
        competition: 'Sutomo 1 Senior High School Programming Competition 2020',
        award: '2<sup>nd</sup> Rank',
        medal: 'silver',
        host: 'SMA Sutomo 1 Medan',
        date: 'Feb. 2020',
      }
    ]
  },
  {
    year: 2019,
    awards: [
      {
        competition: 'Sutomo 1 Junior High Programming Competition 2019',
        award: '1<sup>st</sup> Rank',
        medal: 'gold',
        host: 'SMP Sutomo 1 Medan',
        date: 'Feb. 2019',
      }
    ]
  },
  {
    year: 2018,
    awards: [
      {
        competition: 'Bebras Indonesia Challenge 2018 for Junior High Students, Round 2',
        award: '1<sup>st</sup> Rank',
        medal: 'gold',
        host: 'Bebras Indonesia',
        date: 'Nov. 2018',
      },
      {
        competition: 'Sutomo 1 Junior High Programming Competition 2018',
        award: '2<sup>nd</sup> Rank',
        medal: 'silver',
        host: 'SMP Sutomo 1 Medan',
        date: 'Mar. 2018',
      }
    ]
  }
]

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
          <div class="w-full">
            <swiper
              @swiper="onYearSwiper"
              :spaceBetween="30"
              :slidesPerView="'auto'"
              :freeMode="true"
              :mousewheel="true"
              :modules="modules"
            >
              <swiper-slide v-for="(achievementGroup, index) in achievements" :key="index" class="max-w-[3rem]" @click="achievementSlideToYear(achievementGroup.year)">
                <p class="text-center hover:cursor-pointer" :class="{ 'border-primary border-b-2': achievementGetActiveYear() === achievementGroup.year }" v-html="achievementGroup.year"></p>
              </swiper-slide>
            </swiper>
          </div>

<!--          <div class="join">-->
<!--            <button class="join-item btn">«</button>-->
<!--            <button class="join-item btn">»</button>-->
<!--          </div>-->
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
          <swiper-slide v-for="(achievementGroup, index) in achievements" :key="index" class="max-w-fit">
            <div class="grid gap-4 grid-rows-4 grid-flow-col overflow-auto">
              <AchievementCard v-for="(achievement, index) in achievementGroup.awards"
                               :key="index" :competition="achievement.competition"
                               :award="achievement?.award"
                               :medal="achievement.medal"
                               :host="achievement.host"
                               :date="achievement.date" />
            </div>
          </swiper-slide>
          <swiper-slide class="max-w-fit">
            <div class="w-48"></div>
          </swiper-slide>
        </swiper>
      </div>
    </div>

    <ArrowDown :theme="props.theme" :isHome="false" />
  </div>

</template>

<style>
</style>