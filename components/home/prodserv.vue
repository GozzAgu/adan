<script setup>
import { ref, computed } from 'vue';

const activeTab = ref('power');

const isPowerTab = computed(() => activeTab.value === 'power');
const isEnergyTab = computed(() => activeTab.value === 'energy');

const services = [
  { 
    title: "L8 Compliance & Water Treatment",
    icon: "mdi:water-check", 
    description: "Ensuring your systems meet the necessary legal and health regulations concerning water hygiene and Legionella control.", 
    image: "https://martinlishman.com/wp-content/uploads/MiniTemp-Crop-Temperature-Monitor.jpg" 
  },
  { 
    title: "CWST Inspections & Cleaning ",
    icon: "mdi:water-pump", 
    description: "Conducting thorough inspections and cleaning of Cold Water Storage Tanks (CWST) to maintain water quality and prevent contamination.", 
    image: "https://ml5mxeitll4f.i.optimole.com/w:1091/h:1500/q:mauto/https://tankanddrain.ie/wp-content/uploads/2023/06/coldwater.png" 
  },
  { 
    title: "Temperature Monitoring", 
    icon: "mdi:thermometer",
    description: "Regular monitoring of hot and cold water systems to ensure they function within the required temperature ranges for safety and efficiency.", 
    image: "https://phoenixservicesltd.co.uk/wp-content/uploads/2019/12/hotwater-system-698x1024.jpg" 
  },
  { 
    title: "Risk Assessments & Surveys",
    icon: "mdi:clipboard-check", 
    description: "Identifying potential risks in your water and heating systems and providing solutions to mitigate those risks.", 
    image: "https://images.unsplash.com/photo-1595448831936-822eeb8b5695?q=80&w=3479&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Consultancy & Diagnostics", 
    icon: "mdi:account-question",
    description: "Offering expert advice and diagnostic services to optimize system performance and resolve any issues that may arise.", 
    image: "https://images.unsplash.com/photo-1557426272-fc759fdf7a8d?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Closed & Opened System Management", 
    icon: "mdi:home-modern", 
    description: "Managing both closed and open systems to ensure they are properly maintained, preventing issues such as corrosion, scale buildup, and energy inefficiency.", 
    image: "https://images.unsplash.com/photo-1715635795252-38b8f66026d6?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  }
];
</script>

<template>
  <section class="bg-zinc-100 dark:bg-zinc-900 py-5 md:py-20 px-6">
    <div class="max-w-7xl mx-auto md:px-6">
      <h2 class="text-xl md:text-4xl font-extrabold text-gray-800 dark:text-gray-200 mb-5 border-l-4 border-red-500 dark:border-red-600 pl-4">Services</h2>
      <h3 class="my-4 text-gray-700 dark:text-white">ABAN 1 Solutions offers an extensive range of services designed to meet diverse client needs with precision and excellence:</h3>
      <div class="flex border-b border-gray-300 dark:border-gray-700">
        <button 
          class="tab-button" 
          :class="{ active: isPowerTab }" 
          @click="activeTab = 'power'"
        >
            🌱 Water Hygiene & Compliance
        </button>
        <button 
          class="tab-button" 
          :class="{ active: isEnergyTab }" 
          @click="activeTab = 'energy'"
        >
          ⚡ System Analysis & Management
        </button>
      </div>

      <div class="mt-12 grid md:grid-cols-3 gap-6">
        <div v-if="isPowerTab" v-for="(service, index) in services.slice(0, 3)" :key="index" class="card">
          <img :src="service.image" alt="service.title" class="card-img">
          <div class="p-4 md:p-6">
            <h3 class="card-title flex items-center">
              <span :class="service.icon"></span>
              {{ service.title }}
            </h3>
            <p class="card-text">{{ service.description }}</p>
            <NuxtLink :to="`/services?highlight=${index}`" class="card-link">Learn more</NuxtLink>
          </div>
        </div>

        <div v-if="isEnergyTab" v-for="(service, index) in services.slice(3, 6)" :key="index" class="card">
          <img :src="service.image" alt="service.title" class="card-img">
          <div class="p-4 md:p-6">
            <h3 class="card-title flex items-center gap-2">
              <span :class="service.icon"></span>
              {{ service.title }}
            </h3>
            <p class="card-text">{{ service.description }}</p>
            <NuxtLink :to="`/services?highlight=${index + 3}`" class="card-link">Learn more</NuxtLink>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.tab-button {
  @apply text-gray-700 dark:text-gray-300 text-xs md:text-sm font-semibold px-2 py-1 border-b-4 border-transparent transition-all;
}
.tab-button.active {
  @apply border-gray-500 text-gray-500 dark:text-gray-200;
}

.card {
  @apply bg-white rounded-md dark:bg-black overflow-hidden shadow-sm transition-transform duration-200 ease-out;
  will-change: transform;
}
.card:hover {
  @apply scale-[1.02] shadow-lg;
}

.card-img {
  @apply w-full h-56 object-cover;
}
.card-title {
  @apply text-sm md:text-lg font-semibold text-gray-900 dark:text-gray-100 flex items-center;
}
.card-text {
  @apply text-xs md:text-sm text-gray-600 dark:text-gray-300 mt-2;
}
.card-link {
  @apply text-xs md:text-base text-red-800 font-semibold mt-4 inline-flex items-center gap-2 transition-all;
}
.card-link::after {
  content: " →";
  transition: transform 150ms ease-out;
}
.card-link:hover::after {
  transform: translateX(4px);
}

.tab-button.active {
  @apply border-gray-500 text-gray-500 dark:text-gray-200 dark:border-gray-500;
}
</style>