<template>
  <section class="bg-gray-100 dark:bg-gray-900 min-h-screen">
    <div class="relative w-full h-72 flex items-center justify-center bg-gray-800 text-white">
      <div class="text-center">
        <h1 class="text-4xl md:text-5xl font-bold">Join Our Team</h1>
        <p class="mt-2 text-lg text-gray-300">
          Explore exciting opportunities and grow your career with us.
        </p>
      </div>
    </div>

    <div class="max-w-6xl mx-auto py-16 px-6">
      <h2 class="text-3xl font-bold text-gray-800 dark:text-gray-200 mb-6">Current Openings</h2>

      <div v-if="jobs.length" class="grid md:grid-cols-2 gap-6">
        <div v-for="job in jobs" :key="job.id" class="bg-white dark:bg-gray-800 p-6 rounded-lg shadow-lg">
          <h3 class="text-2xl font-semibold text-gray-900 dark:text-white">{{ job.title }}</h3>
          <p class="text-gray-700 dark:text-gray-300 mt-2">{{ job.description }}</p>
          <p class="text-gray-600 dark:text-gray-400 mt-1">Location: {{ job.location }}</p>
          <button @click="apply(job)"
            class="mt-4 bg-blue-600 hover:bg-blue-700 text-white px-6 py-2 rounded-md font-semibold transition-all">
            Apply Now
          </button>
        </div>
      </div>

      <p v-else class="text-gray-600 dark:text-gray-400 text-center mt-8">No job openings available at the moment.</p>
    </div>

    <div class="text-center bg-blue-600 text-white py-10">
      <h3 class="text-2xl font-bold">Can't find a role that suits you?</h3>
      <p class="mt-2">Send us your resume, and we'll get in touch when a suitable role opens up!</p>
      <button class="mt-4 bg-white text-blue-600 px-6 py-2 rounded-md font-semibold hover:bg-gray-200 transition-all">
        Send Resume
      </button>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const jobs = ref([
  { id: 1, title: "Frontend Developer", description: "Build amazing UI with Vue & Nuxt.", location: "Remote" },
  { id: 2, title: "Backend Engineer", description: "Develop scalable APIs and backend services.", location: "On-site" },
  { id: 3, title: "UI/UX Designer", description: "Design beautiful user experiences.", location: "Hybrid" }
]);

const apply = (job) => {
  alert(`You are applying for: ${job.title}`);
};
</script>