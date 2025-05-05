<template>
  <section class="relative w-full h-screen flex items-center justify-center text-white overflow-hidden">
    <div class="absolute inset-0">
      <Swiper
        :modules="[Autoplay, Navigation]"
        :slides-per-view="1"
        :loop="true"
        :autoplay="{ delay: 5000, disableOnInteraction: false }"
        class="w-full h-full"
      >
        <SwiperSlide v-for="(image, index) in images" :key="index" class="relative">
          <img :src="image" alt="Energy Future" class="w-full h-full object-cover">
          <div class="absolute inset-0 bg-gradient-to-b from-black/60 via-black/40 to-black/60"></div>
        </SwiperSlide>
      </Swiper>
    </div>

    <div ref="content" class="relative text-center px-6 z-10 max-w-3xl opacity-0">
      <h1 ref="heading" class="text-4xl md:text-6xl font-bold uppercase leading-tight">
        Safety for your environment
      </h1>
      <p ref="paragraph" class="mt-4 text-lg md:text-xl text-gray-200">
        We are committed to providing reliable, high-quality services that help you stay compliant, ensure system performance, and protect the health and safety of your environment.
      </p>
      <div ref="buttonContainer" class="mt-6">
        <NuxtLink to="/about" class="cta-button">Learn More</NuxtLink>
      </div>
    </div>
  </section>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Autoplay, Navigation } from "swiper/modules";
import gsap from "gsap";
import { onMounted, ref } from "vue";
import "swiper/css";
import "swiper/css/navigation";

const images = [
  "https://images.unsplash.com/photo-1657368567330-662b92e03dcc?q=80&w=3432&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
  // "https://images.unsplash.com/photo-1532787799187-93655e51d472?q=80&w=3474&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D",
];

const content = ref(null);
const heading = ref(null);
const paragraph = ref(null);
const buttonContainer = ref(null);

onMounted(() => {
  gsap.to(content.value, { opacity: 1, duration: 1 });

  gsap.from(heading.value, {
    y: 50,
    opacity: 0,
    duration: 1,
    ease: "power3.out",
    delay: 0.3,
  });

  gsap.from(paragraph.value, {
    y: 30,
    opacity: 0,
    duration: 1,
    ease: "power3.out",
    delay: 0.6,
  });

  gsap.from(buttonContainer.value, {
    y: 20,
    opacity: 0,
    duration: 1,
    ease: "power3.out",
    delay: 0.9,
  });
});
</script>

<style scoped>
.cta-button {
  @apply bg-red-900 rounded-md hover:bg-red-700 text-white px-6 py-3 text-sm font-semibold transition-all duration-300;
}

:deep(.swiper-button-next), :deep(.swiper-button-prev) {
  color: white;
  transition: opacity 0.3s;
}
:deep(.swiper-button-next:hover), :deep(.swiper-button-prev:hover) {
  opacity: 0.8;
}
</style>