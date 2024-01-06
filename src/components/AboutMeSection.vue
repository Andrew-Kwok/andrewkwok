<script setup>
import 'swiper/css';

import { Swiper, SwiperSlide } from 'swiper/vue';
import { Autoplay, Pagination } from "swiper/modules";
import ArrowDown from "@/components/ScrollAnimation/ArrowDown.vue";

const props = defineProps({
  theme: String,
});

const aboutMe = [
  {
    title: 'Computer Science Undergraduate',
    description: 'I am currently pursuing a Bachelor of Science in Computer Science at the University of Toronto. I have received a full-ride scholarship, <em>Beasiswa Indonesia Maju</em>, from the Indonesian government for my study in Canada.',
  },
  {
    title: 'Software Engineer',
    description: 'I love to explore and build things. I have experience in building web applications and backend API services.',
  },
  {
    title: 'Competitive Programmer',
    description: 'I have been doing competitive programming since 2017. My notable achievements are bronze medalist of IOI 2022 and gold medalist of Indonesia\'s NOI 2020.',
  }
]

const education = [
  {
    title: 'Sutomo 1 Medan',
    description: 'I had my elementary, middle, and high school education here. I developed my interest in competitive programming during my middle school, and has since been actively participating in various competitions.',
    duration: '2010 - 2022',
    image: {
      src: '/logo-sutomo.png',
      alt: 'Sutomo 1 Medan',
    }
  },
  {
    title: 'University of Toronto',
    description: 'I am currently enrolled in Computer Science Specialist and Economics Minor program. My expected graduation is in June 2026.',
    duration: '2022 - present',
    image: {
      src: './logo-uoft.svg',
      alt: 'University of Toronto',
    }
  },
]

const modules = [Autoplay, Pagination];
const pagination = {
  el: ".about-me-swiper-pagination",
  clickable: true,
  renderBullet: function (index, className) {
    return `<li class="avatar ${className}" data-slide="${index}" @click="handleSlideClick(${index})">
              <div class="m-2 w-16 h-16 btn p-0">
                <img src="${education[index]?.image?.src}" alt="${education[index]?.image?.alt}" />
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
        <div v-for="(info, index) in aboutMe" :key="index" class="collapse collapse-arrow bg-base-200 m-4 my-8">
          <input type="radio" name="my-accordion-2" checked="checked" />
          <h1 v-html="info.title" class="collapse-title text-xl font-medium"></h1>
          <div class="collapse-content">
            <p v-html="info.description"> </p>
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
          <swiper-slide v-for="(info, index) in education" :key="index">
            <h1 v-html="info.title" class="text-4xl font-bold"></h1>
            <p v-html="info.duration"></p>
            <div class="divider"></div>
            <p v-html="info.description"></p>
          </swiper-slide>
        </swiper>
        <ul class="about-me-swiper-pagination absolute right-0">
        </ul>
      </div>
    </div>
    <ArrowDown :theme="props.theme" :isHome="false" />
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