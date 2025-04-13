<template>
  <section class="relative w-full pb-32 bg-gray-100 dark:bg-black text-gray-800 dark:text-gray-200">
    <div class="relative w-full h-72 flex items-center justify-center bg-gray-900 text-white">
      <div class="text-center">
        <h1 class="text-4xl md:text-5xl font-bold">Our Services</h1>
        <p class="mt-2 text-lg text-gray-300">
          Visioni & Strauss offers an extensive range of services designed to meet diverse client needs with precision and excellence.
        </p>
      </div>
    </div>

    <div class="max-w-7xl mx-auto mt-12 px-6 grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-12">
      <div v-for="(service, index) in services" :key="index" class="service-card">
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
</style>