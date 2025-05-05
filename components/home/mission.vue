<template>
  <section ref="sectionRef" class="relative w-full bg-zinc-200 dark:bg-zinc-950 py-12 md:py-20 transition-colors duration-300">
    <div class="max-w-7xl mx-auto px-6">
      <h2 ref="titleRef" class="text-xl md:text-4xl font-extrabold text-gray-700 dark:text-gray-200 mb-5 border-l-4 border-red-500 dark:border-red-600 pl-4 opacity-0">
        Our Vision & Mission
      </h2>

      <div ref="cardWrapperRef" class="grid grid-cols-1 md:grid-cols-2 gap-12 opacity-0">
        <div ref="visionCardRef" class="info-card vision-card opacity-0">
          <h3>Our Vision</h3>
          <p>
            We aspire to be the most preferred integrated solution partner by continuously building 
            on our experience and embracing innovation to drive sustainable progress.
          </p>
        </div>
        <div ref="missionCardRef" class="info-card mission-card opacity-0">
          <h3>Our Mission</h3>
          <p>
            To ensure water quality and regulatory compliance with unwavering professionalism and integrity. 
            We deliver reliable testing, expert guidance, and sustainable solutions to safeguard public 
            health and protect the environment.
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
const cardWrapperRef = ref(null);
const visionCardRef = ref(null);
const missionCardRef = ref(null);

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

    timeline.to(cardWrapperRef.value, {
      opacity: 1,
      duration: 0.5,
      ease: "power3.out",
    });

    timeline.to([visionCardRef.value, missionCardRef.value], {
      opacity: 1,
      y: 0,
      stagger: 0.3,
      duration: 0.8,
      ease: "power3.out",
    });
  });
});
</script>

<style scoped>
.info-card {
  @apply p-8 rounded-lg backdrop-blur-md transition-transform duration-300 bg-white dark:bg-black border-2 opacity-0;
}

h3 {
  @apply text-lg md:text-2xl font-bold mb-4 uppercase tracking-wide text-gray-700 dark:text-gray-400;
}

p {
  @apply text-xs md:text-sm text-gray-700 dark:text-gray-400 leading-relaxed;
}
</style>