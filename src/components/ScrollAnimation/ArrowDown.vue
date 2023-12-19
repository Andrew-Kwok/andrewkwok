<script setup>
import lottie from 'lottie-web';
import { onMounted, onBeforeUnmount, ref, defineProps, watchEffect, watch } from "vue";

// theme is mandatory
let props = defineProps(['theme', 'color', 'isHome']);
const color = ref(props.color || props.theme.value === 'dark' ? 'white' : 'black');

const lottieContainer = ref(null);
const lottieWrapper = ref(null);
let animation;

const loadAnimation = () => {
  animation = lottie.loadAnimation({
    container: lottieContainer.value,
    renderer: 'svg',
    loop: true,
    autoplay: true,
    path: `arrow-down-animation-${color.value}.json`,
  });
};

const updateLottieContainerHeight = () => {
  lottieWrapper.value.style.bottom = Math.min(64, window.innerHeight * 0.05) + 'px';
  lottieContainer.value.style.height = Math.min(72, window.innerHeight * 0.03) + 'px';
  if (animation) {
    animation.resize();
  }
};

onMounted(() => {
  loadAnimation();
  updateLottieContainerHeight();

  window.addEventListener('resize', updateLottieContainerHeight);
});

watchEffect(() => {
  color.value = props.theme === 'dark' ? 'white' : 'black';

  if (animation) {
    animation.destroy();
  }
  loadAnimation();
})

onBeforeUnmount(() => {
  if (animation) {
    animation.destroy();
  }

  window.removeEventListener('resize', updateLottieContainerHeight);
});

</script>

<template>
  <div ref="lottieWrapper" class="absolute bottom-16">
    <div class="text-center" v-if="props.isHome">
      <p class="text-2xl"> Scroll down to learn more about me! </p>
      <p class="text-2xl"> ... or check my <a href="https://google.com" class="font-bold underline link">CV</a> instead </p>
    </div>
    <div class="mt-4" ref="lottieContainer"></div>
  </div>
</template>

<style scoped>

</style>