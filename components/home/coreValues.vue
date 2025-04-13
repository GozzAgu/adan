<template>
  <section class="relative w-full pt-16 pb-32 bg-gray-100 dark:bg-black text-gray-800 dark:text-gray-200">
    <div class="max-w-7xl mx-auto px-6">
      <h2 class="text-xl md:text-4xl font-extrabold text-gray-900 dark:text-gray-200 mb-5 border-l-4 border-red-500 dark:border-red-600 pl-4">
        Our Core Values
      </h2>
      <h4 class="text-xs md:text-lg text-gray-600 dark:text-gray-300 mb-8 tracking-wide">
        The principles that drive our mission and define our success.
      </h4>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6 p-6 max-w-7xl mx-auto">
      <div v-for="(value, index) in coreValues" :key="index" class="value-card">
        <div class="icon-container">
          <Icon :name="value.icon" class="text-red-500 dark:text-red-400 text-4xl" />
        </div>
        <h3 class="text-lg font-semibold text-gray-900 dark:text-gray-100 mt-4">{{ value.title }}</h3>
        <p class="text-sm text-gray-600 dark:text-gray-300 mt-2">{{ value.description }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const coreValues = [
  { title: "Transparency", icon: "mdi:eye-outline", description: "Upholding open communication and accountability in every project." },
  { title: "Trust", icon: "mdi:handshake-outline", description: "Building lasting relationships through consistent, dependable performance." },
  { title: "Innovation", icon: "mdi:lightbulb-outline", description: "Embracing technology and creative solutions to address evolving challenges." },
  { title: "Teamwork", icon: "mdi:account-group-outline", description: "Harnessing collective expertise to lead by example." },
  { title: "Quality", icon: "mdi:check-decagram-outline", description: "Demonstrating an unwavering commitment to excellence from project inception to completion." }
];
</script>

<style scoped>
.value-card {
  @apply flex flex-col items-center p-6 rounded-xl bg-white dark:bg-gray-900 transition-all duration-300 text-center;
  backdrop-filter: blur(20px);
}

.icon-container {
  @apply flex items-center justify-center w-16 h-16 bg-red-100 dark:bg-red-900 rounded-full;
}
</style>