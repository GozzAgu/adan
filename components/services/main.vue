<template>
  <section class="relative w-full pb-32 bg-gray-100 dark:bg-black text-gray-800 dark:text-gray-200">
    <div class="relative w-full h-72 flex items-center justify-center bg-gray-900 text-white">
      <div class="text-center">
        <h1 class="text-4xl md:text-5xl font-bold">Our Services</h1>
        <p class="mt-2 text-lg text-gray-300">
          ABAN 1 Solutions offers an extensive range of services designed to meet diverse client needs with precision and excellence.
        </p>
      </div>
    </div>

    <div class="max-w-7xl mx-auto mt-12 px-6 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-12">
      <div
        v-for="(service, index) in services"
        :key="index"
        class="service-card"
        :class="{ 'highlighted-service': highlightIndex === index }"
      >
        <div class="relative w-full h-48 overflow-hidden rounded-lg">
          <img :src="service.image" :alt="service.title" class="w-full h-full object-cover">
        </div>
        <div class="text-center mt-4">
          <div class="icon-container">
            <Icon :name="service.icon" class="text-red-500 dark:text-red-400 text-4xl" />
          </div>
          <h3 class="text-lg font-semibold text-gray-900 dark:text-gray-100 mt-4">{{ service.title }}</h3>
          <p class="text-sm text-gray-600 dark:text-gray-300 mt-2">{{ service.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { useRoute } from 'vue-router'

const route = useRoute()
const highlightIndex = ref(null)

onMounted(() => {
  const highlightParam = route.query.highlight
  if (highlightParam !== undefined) {
    highlightIndex.value = parseInt(highlightParam)
    setTimeout(() => {
      highlightIndex.value = null
    }, 2000)
  }
})

const services = [
  { 
    title: "L8 Compliance & Water Treatment",
    icon: "mdi:water-check", 
    description: "Ensuring your systems meet the necessary legal and health regulations concerning water hygiene and Legionella control.", 
    image: "https://images.unsplash.com/photo-1533077162801-86490c593afb?q=80&w=3474&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "CWST Inspections & Cleaning ",
    icon: "mdi:water-pump", 
    description: "Conducting thorough inspections and cleaning of Cold Water Storage Tanks (CWST) to maintain water quality and prevent contamination.", 
    image: "https://images.unsplash.com/photo-1627098241506-344dea0aa27b?q=80&w=3431&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
  },
  { 
    title: "Temperature Monitoring", 
    icon: "mdi:thermometer",
    description: "Regular monitoring of hot and cold water systems to ensure they function within the required temperature ranges for safety and efficiency.", 
    image: "https://images.unsplash.com/photo-1619140099965-06d74aaf51fa?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" 
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

<style scoped>
.service-card {
  @apply flex flex-col items-center p-6 rounded-xl bg-white dark:bg-gray-900 shadow-lg hover:shadow-2xl transition-all duration-300 text-center;
}

.icon-container {
  @apply flex items-center justify-center w-16 h-16 bg-red-100 dark:bg-red-900 rounded-full mx-auto;
}

.service-card img {
  @apply w-full h-48 object-cover rounded-lg;
}

.highlighted-service {
  @apply ring-4 ring-red-700 scale-105 transition-all duration-300;
}
</style>