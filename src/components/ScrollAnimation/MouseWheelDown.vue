<script setup>
import lottie from 'lottie-web';
import { onMounted, onBeforeUnmount, ref } from "vue";

const lottieContainer = ref(null);
const lottieWrapper = ref(null);
let animation;

const updateLottieContainerHeight = () => {
  lottieWrapper.value.style.bottom = Math.min(64, window.innerHeight * 0.05) + 'px';
  lottieContainer.value.style.height = Math.min(144, window.innerHeight * 0.2) + 'px';
  if (animation) {
    animation.resize();
  }
};

onMounted(() => {
  animation = lottie.loadAnimation({
    container: lottieContainer.value,
    renderer: 'svg',
    loop: true,
    autoplay: true,
    path: 'mousewheel-animation-black.json',
  });

  updateLottieContainerHeight();
  window.addEventListener('resize', updateLottieContainerHeight);
});

onBeforeUnmount(() => {
  if (animation) {
    animation.destroy();
  }

  window.removeEventListener('resize', updateLottieContainerHeight);
});
</script>

<template>
  <div ref="lottieWrapper" class="absolute bottom-16">
    <div ref="lottieContainer"></div>
  </div>
</template>

<style scoped>

</style>