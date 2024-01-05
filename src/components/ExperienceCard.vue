<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";

const swiperModules = [];

let swiperInstance = ref();
const onSwiper = (swiper) => {
  swiperInstance.value = swiper;
};

const slidePrev = () =>   {
  swiperInstance.value.slidePrev();
};

const slideNext = () =>   {
  swiperInstance.value.slideNext();
};

const slideToIndex = (index) =>   {
  swiperInstance.value.slideTo(index);
};

const getActiveIndex = () => {
  return swiperInstance.value?.activeIndex;
};


</script>

<template>
  <swiper
    @swiper="onSwiper"
    :space-between="100"
    :grabCursor="true"
    :pagination="true"
    :navigation="true"
    :modules="swiperModules"
    class="max-w-5xl"
  >
    <swiper-slide>
      <div class="card lg:card-side bg-base-200 shadow-xl w-full p-2">
        <figure><img src="govtech-procurement-logo.png" class="h-[200px] object-cover" alt="Govtech"/></figure>
        <div class="card-body">
          <h2 class="card-title"> GovTech Procurement </h2>
          <h1> Software Engineer Intern - Backend  </h1>
          <p> May. 2023 - Sep. 2023 </p>
          <div class="divider"> </div>
          <p> Utilized: Go, Auth0, GraphQL, PostgreSQL, Redis, Google Cloud Services, etc.  </p>
        </div>
      </div>
    </swiper-slide>
    <swiper-slide>
      <div class="card lg:card-side bg-base-200 shadow-xl max-w-5xl">
        <figure><img src="govtech-procurement-logo.png" class="h-[200px] object-cover" alt="Govtech"/></figure>
        <div class="card-body">
          <h2 class="card-title"> GovTech Procurement </h2>
          <h1> Software Engineer Intern - Backend  </h1>
          <p> May. 2023 - Sep. 2023 </p>
          <div class="divider"> </div>
          <p> Utilized: Go, Auth0, GraphQL, PostgreSQL, Redis, Google Cloud Services, etc.  </p>
        </div>
      </div>
    </swiper-slide>
    <swiper-slide>
      <div class="card lg:card-side bg-base-200 shadow-xl max-w-5xl">
        <figure><img src="govtech-procurement-logo.png" class="h-[200px] object-cover" alt="Govtech"/></figure>
        <div class="card-body">
          <h2 class="card-title"> GovTech Procurement </h2>
          <h1> Software Engineer Intern - Backend  </h1>
          <p> May. 2023 - Sep. 2023 </p>
          <div class="divider"> </div>
          <p> Utilized: Go, Auth0, GraphQL, PostgreSQL, Redis, Google Cloud Services, etc.  </p>
        </div>
      </div>
    </swiper-slide>
  </swiper>

  <div class="flex justify-center mt-2">
    <div class="join">
      <button class="join-item btn" :class="{ 'btn-disabled' : getActiveIndex() === 0 }" @click="slidePrev()" >«</button>
      <button class="join-item btn">Page {{1 + getActiveIndex()}} of 3</button>
      <button class="join-item btn" :class="{ 'btn-disabled' : getActiveIndex() === 2 }" @click="slideNext()" >»</button>
    </div>
  </div>

</template>
