<script setup >
import { onMounted, ref } from "vue";

import Navbar from '@/components/NavBar.vue'
import HomeSection from "@/components/HomeSection.vue";
import EducationSection from "@/components/EducationSection.vue";
import ExperienceSection from "@/components/ExperienceSection.vue";
import ProjectSection from "@/components/ProjectSection.vue";
import ContactSection from "@/components/ContactSection.vue";
import AchievementSection from "@/components/AchievementSection.vue";

import "swiper/css";
// import "swiper/css/pagination";

import { Swiper, SwiperSlide } from "swiper/vue";
import { Mousewheel, Pagination} from "swiper/modules";

const sections = ['home', 'education', 'experience', 'achievement', 'project', 'contact']

const swiperModules = [Mousewheel, Pagination];
const pagination = {
  el: ".swiper-pagination",
  clickable: true,
  renderBullet: function (index, className) {
    return `<li class="${className} text-gray-100 btn btn-ghost" data-slide="${index}" @click="handleSlideClick(${index})">${sections[index].charAt(0).toUpperCase() + sections[index].slice(1)}</li>`;
  },
};

</script>

<template>
  <Navbar />
  <swiper @swiper="getRef"
      :direction="'vertical'"
      :slidesPerView="1"
      :spaceBetween="0"
      :mousewheel="true"
      :pagination="pagination"
      :modules="swiperModules"
  >
      <swiper-slide id="home">
        <HomeSection />
      </swiper-slide>
      <swiper-slide id="education">
        <EducationSection />
      </swiper-slide>
      <swiper-slide>
        <ExperienceSection />
      </swiper-slide>
      <swiper-slide>
        <AchievementSection />
      </swiper-slide>
      <swiper-slide>
        <ProjectSection />
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
