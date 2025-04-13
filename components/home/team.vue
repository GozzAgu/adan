<template>
  <section class="relative w-full pt-16 pb-32 dark:bg-black text-gray-300 dark:text-gray-200">
    <div class="max-w-7xl mx-auto px-6">
      <h2 class="text-xl md:text-4xl font-extrabold text-gray-700 dark:text-gray-200 mb-5 border-l-4 border-red-500 dark:border-red-600 pl-4">
        Meet Our Team
      </h2>
      <h4 class="text-xs md:text-lg text-gray-600 dark:text-gray-200 mb-4 tracking-wide">
        Passionate professionals dedicated to excellence.
      </h4>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-3 md:grid-cols-5 gap-8 p-6 max-w-7xl mx-auto mt-12">
      <div v-for="(member, index) in teamMembers" :key="index" class="team-card">
        <h3 class="text-xs md:text-sm font-semibold mt-4 text-gray-600 dark:text-gray-100">{{ member.name }}</h3>
        <p class="text-xs text-gray-400 dark:text-gray-300">{{ member.role }}</p>
        <div class="flex space-x-4 mt-4">
          <a v-if="member.linkedin" :href="member.linkedin" target="_blank" class="icon">
            <Icon name="mdi:linkedin" class="text-blue-400 dark:text-blue-300 text-2xl" />
          </a>
          <a v-if="member.twitter" :href="member.twitter" target="_blank" class="icon">
            <Icon name="mdi:twitter" class="text-blue-300 dark:text-blue-400 text-2xl" />
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const teamMembers = [
  {
    name: "Arch. Ositadinma Christopher",
    role: "CEO & Founder",
    image: "",
  },
  {
    name: "Engr. Okey Mike Nwubani",
    role: "CTO",
    image: "",
  },
  {
    name: "Engr. Olalekan Akinwale Famakinwa",
    role: "Lead Developer",
    image: "",
  },
  {
    name: "Engr. Opadere Ezekiel Segun",
    role: "CEO & Founder",
    image: "",
  },
  {
    name: "Obinna Francis Nwokoro",
    role: "CTO",
    image: "",
  }
];
</script>

<style scoped>
.team-card {
  @apply flex flex-col p-6 rounded-lg transition-transform duration-300 bg-gray-100 dark:bg-red-900;
  backdrop-filter: blur(10px);
}

.icon {
  @apply p-2 rounded-full bg-gray-800 hover:bg-gray-700 dark:bg-gray-600 dark:hover:bg-gray-500 transition-all;
}
</style>