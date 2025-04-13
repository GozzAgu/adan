<script setup>
import { ref, computed } from 'vue';

const activeTab = ref('power');

const isPowerTab = computed(() => activeTab.value === 'power');
const isEnergyTab = computed(() => activeTab.value === 'energy');

const services = [
  { 
    title: "Gas Products & Chemical Supply", 
    icon: "mdi:gas-cylinder", 
    description: "Reliable, quality-assured gas and chemical supply for energy and industrial applications.", 
    image: "https://images.unsplash.com/photo-1510467181625-c419e443bdfa?q=80&w=3538&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Road Construction & Infrastructure", 
    icon: "mdi:road-variant", 
    description: "Building durable roads, bridges, culverts, and drainage systems for sustainable transport networks.", 
    image: "https://images.unsplash.com/photo-1503708928676-1cb796a0891e?q=80&w=2048&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Solar Power & Renewable Energy", 
    icon: "mdi:solar-power", 
    description: "Cutting-edge solar energy solutions for cost-effective and sustainable power generation.", 
    image: "https://images.unsplash.com/photo-1558449028-b53a39d100fc?q=80&w=3474&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Renovation & Building Works", 
    icon: "mdi:hammer-wrench", 
    description: "Modernizing structures with a focus on functionality, safety, and aesthetic excellence.", 
    image: "https://images.unsplash.com/photo-1508450859948-4e04fabaa4ea?q=80&w=3024&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Water & Sewage Engineering", 
    icon: "mdi:water-pump", 
    description: "Advanced water management and sewage treatment solutions for safe and sustainable water use.", 
    image: "https://images.unsplash.com/photo-1582669300365-630322b86cf9?q=80&w=3542&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Civil Engineering & Estate Planning", 
    icon: "mdi:home-modern", 
    description: "Comprehensive civil engineering services for estate planning and development.", 
    image: "https://images.unsplash.com/photo-1625722662233-297060231b85?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "General Supplies", 
    icon: "mdi:package-variant-closed", 
    description: "Providing essential supplies to support seamless project execution.", 
    image: "https://images.unsplash.com/photo-1627309366653-2dedc084cdf1?q=80&w=3466&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  }
];
</script>

<template>
  <section class="bg-zinc-100 dark:bg-zinc-900 py-5 md:py-20 px-6">
    <div class="max-w-7xl mx-auto md:px-6">
      <h2 class="text-xl md:text-4xl font-extrabold text-gray-800 dark:text-gray-200 mb-5 border-l-4 border-red-500 dark:border-red-600 pl-4">Services</h2>
      <h3 class="my-4">Visioni & Strauss offers an extensive range of services designed to meet diverse client needs with precision and excellence:</h3>
      <div class="flex border-b border-gray-300 dark:border-gray-700">
        <button 
          class="tab-button" 
          :class="{ active: isPowerTab }" 
          @click="activeTab = 'power'"
        >
          ⚡ Keeping You Powered
        </button>
        <button 
          class="tab-button" 
          :class="{ active: isEnergyTab }" 
          @click="activeTab = 'energy'"
        >
          🌱 Smart Energy Stops
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
            <a href="#" class="card-link">Learn more</a>
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
            <a href="#" class="card-link">Learn more</a>
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