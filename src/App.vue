<script setup >
import { onMounted, ref } from "vue";

import Navbar from '@/components/NavBar.vue'
import HomeSection from "@/components/HomeSection.vue";
import AboutMeSection from "@/components/AboutMeSection.vue";
import ExperienceSection from "@/components/ExperienceSection.vue";
import ContactSection from "@/components/ContactSection.vue";
import AchievementSection from "@/components/AchievementSection.vue";

import "swiper/css";
// import "swiper/css/pagination";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Mousewheel, Pagination} from "swiper/modules";

const sections = ['Home', 'About Me', 'Experience', 'Achievement', 'Contact']

const swiperModules = [Mousewheel, Pagination];
const pagination = {
  el: ".navbar-swiper-pagination",
  clickable: true,
  renderBullet: function (index, className) {
    return `<li class="${className} text-gray-100 btn btn-ghost" data-slide="${index}" @click="handleSlideClick(${index})">${sections[index]}</li>`;
  },
};

const swiperInstance = ref();
const swiperEnabled = ref(true);

const onSwiper = (swiper) => {
  swiperInstance.value = swiper;
};

const slideToHome = () =>   {
  swiperInstance.value.slideTo(0);
};

const startCountdown = () => {
  swiperEnabled.value = false;
  setTimeout(() => {
    swiperEnabled.value = true;
  }, 500);
};

const theme = ref(window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
const toggleTheme = () => {
  theme.value = theme.value === 'dark' ? 'light' : 'dark';
};

</script>

<template>
  <Navbar :theme="theme" :toggleTheme="toggleTheme" :slideToHome="slideToHome" />
  <swiper
    @swiper="onSwiper"
    :direction="'vertical'"
    :slidesPerView="1"
    :spaceBetween="0"
    :freeMode="false"
    :mousewheel="swiperEnabled"
    :pagination="pagination"
    :modules="swiperModules"
  >
      <swiper-slide>
        <HomeSection :theme="theme" />
      </swiper-slide>
      <swiper-slide>
        <AboutMeSection />
      </swiper-slide>
      <swiper-slide>
        <ExperienceSection />
      </swiper-slide>
      <swiper-slide>
        <AchievementSection />
      </swiper-slide>
      <swiper-slide>
        <ContactSection />
      </swiper-slide>
  </swiper>
</template>

<style>
#app {
  height: 100%;
}

html,
body {
  position: relative;
  height: 100%;
  margin: 0;
  padding: 0;
}

.swiper {
  width: 100%;
  height: 100%;
}
</style>
