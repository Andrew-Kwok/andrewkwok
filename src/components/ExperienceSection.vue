<script setup>

import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectFade } from 'swiper/modules';
import ExperienceCard from "@/components/ExperienceCard.vue";

import 'swiper/css';
import 'swiper/css/effect-flip';
import 'swiper/css/effect-fade';
import ArrowDown from "@/components/ScrollAnimation/ArrowDown.vue";

const props = defineProps({
  theme: String,
});

const sections = ["Work", "Project", "Organization & Volunteer"];

const experiences = [
  {
    type: "Work",
    items: [
      {
        company_or_title: "GovTech Procurement",
        logo: "logo-govtech-procurement.png",
        position: "Software Engineer Intern - Backend",
        date: "May. 2023 - Sep. 2023",
        description: "Developed a GraphQL API for a new procurement system using Go, Auth0, PostgreSQL, Redis, and Google Cloud Services.",
      }
    ]
  },
  {
    type: "Project",
    items: [
      {
        company_or_title: "Huawei Challenge Task Cooperation Project",
        logo: "logo-huawei.png",
        position: "Researcher",
        date: "Jul. 2023 - Sep. 2023",
        description: "Worked in a team of 5 and developed an algorithm that achieved 105% performance of OpenBLAS on single threaded GEMM under challenge's input constraint",
      },
      {
        company_or_title: "Perhimpuan Pelajar Sains Nasional (PPSN)",
        logo: "logo-ppsn.png",
        position: "Web Developer",
        date: "Jan. 2023 - Present",
        description: "Developed a multi-purpose website for PPSN using Next.js and Django REST Framework.",
      }
    ]
  },
  {
    type: "Organization & Volunteer",
    items: [
      {
        company_or_title: "Permika Toronto",
        position: "Research and Development Associate",
        date: "Jul. 2023 - Present",
        description: "Indonesian Students’ Association in Toronto, Canada. <br/> Manages membership database, invitation, and feedback forms"
      },
      {
        company_or_title: "Indonesia’s National Olympiad in Informatics (OSN) 2023",
        position: "Head of Training Supervisors",
        date: "Jul. 2023 - Sep. 2023",
        description: "Supervised and managed training for 100 students to compete in OSN 2023."
      },
      {
        company_or_title: "Permika Nasional",
        position: "Visual Media Coordinator",
        date: "Oct. 2022 - Aug. 2023",
        description: "Indonesian Students’ Association in Toronto, Canada. <br/> Designed posters, letters, etc. for social media and organizational uses"
      },
      {
        company_or_title: "Computer Science Student Union",
        position: "Leetcode Nights - General Council",
        date: "Oct. 2022 - Apr. 2023",
        description: "Discussed and made presentations of Leetcode problems."
      },
      {
        company_or_title: "TOKI Regular Open Contest (TROC)",
        position: "Problem Author",
        date: "Feb. 2022 - Feb. 2023",
        description: "Authored problems for TROC#26 and TROC#31 participated by programmers around the world"
      },
      {
        company_or_title: "Indonesia Food Festival (IFF) 2022",
        position: "Volunteer",
        date: "Sep. 2022",
        description: "Helped in the logistics preparation and execution of IFF 2022."
      },
      {
        company_or_title: "P2S1 Computer Olympiad 2022",
        position: "Problem Author",
        date: "Mar. 2022",
        description: "Authored problems and helped organized the contest of the competition."
      },
      {
        company_or_title: "OSIS SMP Sutomo 1",
        position: "Graphics Designer",
        date: "Oct. 2017 - Jun. 2019",
        description: "Designed certificated and posters for organizational uses."
      }
    ]
  }
]

const skills = [];

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
  <div id="experience" class="hero h-screen relative">
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
          <swiper-slide v-for="(exp, index) in experiences" :key="index">
            <div class="w-full flex flex-col justify-center">
              <ExperienceCard :experienceList="exp.items" :theme="theme" />
            </div>
          </swiper-slide>
<!--          <swiper-slide>-->
<!--            <p> Skills </p>-->
<!--          </swiper-slide>-->
        </swiper>
      </div>
    </div>
    <ArrowDown :theme="props.theme" :isHome="false" />
  </div>

</template>

<style scoped>

</style>