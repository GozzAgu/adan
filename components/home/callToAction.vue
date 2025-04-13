<template>
  <section class="relative w-full py-16 flex items-center justify-center bg-gradient">
    <div class="cta-container">
      <h2 class="text-3xl md:text-5xl font-bold text-gray-200 text-center">
        Let's Build Something Amazing Together
      </h2>
      <p class="text-lg text-gray-400 text-center mt-4">
        Join us in shaping the future with innovative solutions tailored for success.
      </p>
      <div class="mt-6 flex justify-center">
        <NuxtLink to="/contact" class="cta-button">Get Started</NuxtLink>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* Animated Gradient Background */
@keyframes gradientShift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.bg-gradient {
  background: linear-gradient(45deg, #000, #18181b, #0f0f0f, #27272a, #000);
  background-size: 300% 300%;
  animation: gradientShift 8s ease infinite;
  box-shadow: 0px 0px 40px rgba(24, 24, 27, 0.5);
}

.cta-container {
  @apply backdrop-blur-md rounded-xl p-8 md:p-12 max-w-7xl transition-all duration-300;
  text-align: center;
}

.cta-button {
  @apply bg-red-900 text-white font-semibold px-6 py-3 rounded-lg text-sm 
  shadow-md hover:scale-105 transition-transform duration-300 hover:bg-zinc-700;
}
</style>