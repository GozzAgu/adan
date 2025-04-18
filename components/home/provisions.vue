<template>
  <section ref="sectionRef" class="relative w-full bg-white dark:bg-black py-20 transition-colors duration-300">
    <div class="max-w-7xl mx-auto px-6">
      <h2 ref="titleRef" class="text-xl md:text-4xl font-extrabold text-gray-800 dark:text-gray-200 mb-5 border-l-4 border-red-500 dark:border-red-600 pl-4 opacity-0">
        Discover Visioni & Strauss
      </h2>

      <p ref="paragraphRef" class="text-gray-700 dark:text-gray-300 text-xs md:text-sm opacity-0">
        ABAN 1 Solutions is a provider of comprehensive services focused on maintaining and optimizing water and heating systems. 
        Our expertise spans across  the water industry ensuring that your systems are compliant, safe, and efficient.
      </p>

      <div ref="cardWrapperRef" class="mt-12 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8 card-wrapper opacity-0">
        <div v-for="(card, index) in cards" :key="index"
          class="bg-white dark:bg-gray-800 p-6 rounded-lg shadow-md transform transition-transform hover:scale-105 hover:shadow-lg card opacity-0">
          <h3 :class="card.color" class="text-xl font-bold text-center">
            {{ card.title }}
          </h3>
          <p class="text-center mt-3 text-gray-600 dark:text-gray-300 text-xs md:text-sm">
            {{ card.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, nextTick } from 'vue';
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

const sectionRef = ref(null);
const titleRef = ref(null);
const paragraphRef = ref(null);
const cardWrapperRef = ref(null);

const cards = ref([
  { title: "Net Zero", description: "Our ambition for 2050, in alignment with global sustainability goals.", color: "text-green-600 dark:text-green-400" },
  { title: "100,000", description: "Innovators and contributors across 120+ countries.", color: "text-blue-600 dark:text-blue-400" },
  { title: "100 Years", description: "Of collective vision, ideas, and relentless drive.", color: "text-red-900" }
]);

onMounted(() => {
  nextTick(() => {
    const timeline = gsap.timeline({
      scrollTrigger: {
        trigger: sectionRef.value,
        start: "top 80%",
        end: "bottom 20%",
        toggleActions: "play none none none",
      },
    });

    timeline.to(titleRef.value, {
      opacity: 1,
      x: 0,
      duration: 0.8,
      ease: "power3.out",
    });

    timeline.to(paragraphRef.value, {
      opacity: 1,
      x: 0,
      duration: 0.8,
      ease: "power3.out",
    }, "-=0.6");

    timeline.to(cardWrapperRef.value, {
      opacity: 1,
      duration: 0.5,
      ease: "power3.out",
    });

    timeline.to('.card', {
      opacity: 1,
      y: 0,
      stagger: 0.2,
      duration: 0.8,
      ease: "power3.out",
    });
  });
});
</script>

<style scoped>
.card-wrapper {
  display: grid;
  gap: 1rem;
}

.card {
  @apply bg-white rounded-md font-semibold dark:bg-zinc-900 shadow-md p-8 border-b-2 transition-transform hover:scale-105 opacity-0;
}

.card:nth-child(1) {
  @apply border-green-400 dark:border-green-500;
}
.card:nth-child(2) {
  @apply border-blue-500 dark:border-blue-600;
}
.card:nth-child(3) {
  @apply border-red-900;
}
</style>