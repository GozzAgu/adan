<template>
  <section class="relative w-full bg-white dark:bg-black py-5 md:py-20 transition-colors duration-300">
    <div class="max-w-7xl mx-auto px-6">
      <h2 class="text-xl md:text-4xl font-extrabold text-gray-800 dark:text-gray-200 mb-10 border-l-4 border-red-500 pl-4">
        Why Choose Us
      </h2>
      <div class="grid grid-cols-1 md:grid-cols-1 gap-12 items-center">
        <div class="choose-us-card">
          <Icon name="material-symbols:person-raised-hand" class="text-green-500 text-4xl" />
          <!-- <h3 class="text-blue-500 dark:text-blue-100 text-lg md:text-2xl font-bold mt-4">Expert Team</h3> -->
          <p class="mt-4 text-gray-600 dark:text-gray-300 leading-relaxed text-xs md:text-sm">
            With years of experience in water testing, compliance, and environmental consulting, 
            we offer reliable, expert solutions that help businesses, cities, and homeowners stay safe, 
            up to code, and environmentally responsible
          </p>
        </div>
        
        <!-- <div class="choose-us-card">
          <Icon name="material-symbols:person-play-rounded" class="text-blue-500 text-4xl" />
          <h3 class="text-red-500 dark:text-red-50 text-lg md:text-2xl font-bold mt-4">Client-Centric Approach</h3>
          <p class="mt-4 text-gray-600 dark:text-gray-300 leading-relaxed text-xs md:text-sm">
            We put our clients first, ensuring that every project is tailored to meet their specific needs. 
            Our commitment to exceptional customer service is at the heart of our success.
          </p>
        </div> -->
      </div>
    </div>
  </section>
</template>

<style scoped>
.choose-us-card {
  @apply bg-white dark:bg-gray-800 p-4 md:p-6 rounded-md;
}

.choose-us-card:nth-child(1) {
  @apply bg-green-50 dark:bg-green-900;
}

.choose-us-card:nth-child(2) {
  @apply bg-blue-50 dark:bg-blue-900;
}

.choose-us-card:nth-child(3) {
  @apply bg-red-50 dark:bg-red-900;
}

.choose-us-card h3 {
  @apply font-semibold;
}
.choose-us-card p {
  @apply text-sm leading-relaxed;
}


.choose-us-card:nth-child(2) .icon {
  @apply bg-blue-100;
}
.choose-us-card:nth-child(3) .icon {
  @apply bg-red-100;
}

@media (min-width: 768px) {
  .choose-us-card .icon {
    width: 70px;
    height: 70px;
  }
}
</style>