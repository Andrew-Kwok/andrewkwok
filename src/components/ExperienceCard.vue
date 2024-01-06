<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";

const props = defineProps({
  experienceList: Array,
  theme: String,
});

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


console.log(props.experienceList[0].logo);

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
    <swiper-slide v-for="(exp, index) in experienceList" :key="index">
      <div class="card lg:card-side bg-base-200 shadow-xl w-full p-2">
        <div class="flex justify-center mt-6 pl-4" v-if="exp.logo !== null && exp.logo !== undefined && exp.logo !== ''">
          <figure class="h-[200px] aspect-square">
            <img class="object-cover" :alt="exp.logo" src="/logo-govtech-procurement.png" v-if="exp.logo === 'logo-govtech-procurement.png'">
            <img class="object-cover" :alt="exp.logo" src="/logo-huawei-dark.png" v-else-if="exp.logo === 'logo-huawei.png' && theme === 'light'" />
            <img class="object-cover" :alt="exp.logo" src="/logo-huawei-light.png" v-else-if="exp.logo === 'logo-huawei.png' && theme === 'dark'" />
            <img class="object-cover" :alt="exp.logo" src="/logo-ppsn.png" v-else-if="exp.logo === 'logo-ppsn.png'" />
          </figure>
        </div>
        <div class="card-body">
          <h2 class="card-title" v-html="exp.company_or_title"></h2>
          <h1 v-html="exp.position"></h1>
          <p v-html="exp.date"></p>
          <div class="divider"> </div>
          <p v-html="exp.description" class="max-w-2xl"></p>
        </div>
      </div>
    </swiper-slide>
  </swiper>

  <div class="flex justify-center mt-2">
    <div class="join">
      <button class="join-item btn" :class="{ 'btn-disabled' : getActiveIndex() === 0 }" @click="slidePrev()" >«</button>
      <button class="join-item btn">Page {{1 + getActiveIndex()}} of {{experienceList.length}}  </button>
      <button class="join-item btn" :class="{ 'btn-disabled' : getActiveIndex() + 1 === experienceList.length }" @click="slideNext()" >»</button>
    </div>
  </div>

</template>
