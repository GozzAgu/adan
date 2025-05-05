<template>
  <div class="min-h-screen flex flex-col bg-gray-50 dark:bg-black transition-all">
    <header class="bg-white dark:bg-black border-b dark:border-b-gray-900 fixed top-0 left-0 w-full z-50 transition-all">
      <div class="container mx-auto flex justify-between items-center py-4 px-6">
        <div class="flex items-center">
          <NuxtLink class="flex items-center gap-x-2" to="/">
            <p class="text-sm md:text-base font-black text-yellow-500">ABAN 1 SOLUTIONS</p>
          </NuxtLink>
        </div>

        <nav class="hidden lg:flex space-x-8">
          <NuxtLink to="/" class="nav-link" :class="{ 'active': isActive('/') }">Home</NuxtLink>
          <NuxtLink to="/about" class="nav-link" :class="{ 'active': isActive('/about') }">About</NuxtLink>
          <NuxtLink to="/contact" class="nav-link" :class="{ 'active': isActive('/contact') }">Contact</NuxtLink>
          <NuxtLink to="/services" class="nav-link" :class="{ 'active': isActive('/services') }">Services</NuxtLink>
          <!-- <NuxtLink to="/careers" class="nav-link" :class="{ 'active': isActive('/careers') }">Careers</NuxtLink> -->
        </nav>

        <div class="flex items-center space-x-4">
          <div class="hidden lg:block">
            <NuxtLink to="/about" class="cta-button">Learn More</NuxtLink>
          </div>
          <button class="icon-btn">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" stroke-width="2"
              viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
              <circle cx="11" cy="11" r="8"></circle>
              <line x1="21" y1="21" x2="16.65" y2="16.65"></line>
            </svg>
          </button>

          <button @click="toggleMenu" class="lg:hidden focus:outline-none">
            <svg class="w-6 h-6 text-gray-700" fill="none" stroke="currentColor" stroke-width="2"
              viewBox="0 0 24 24">
              <path v-if="!menuOpen" d="M4 6h16M4 12h16M4 18h16"></path>
              <path v-else d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </button>
        </div>
      </div>

      <transition name="slide">
        <div v-if="menuOpen" class="lg:hidden bg-white shadow-md absolute w-full left-0 top-full">
          <NuxtLink to="/" class="mobile-link" :class="{ 'active': isActive('/') }">Home</NuxtLink>
          <NuxtLink to="/about" class="mobile-link" :class="{ 'active': isActive('/about') }">About</NuxtLink>
          <NuxtLink to="/contact" class="mobile-link" :class="{ 'active': isActive('/contact') }">Contact</NuxtLink>
          <NuxtLink to="/services" class="mobile-link" :class="{ 'active': isActive('/services') }">Services</NuxtLink>
          <!-- <NuxtLink to="/careers" class="mobile-link" :class="{ 'active': isActive('/careers') }">Careers</NuxtLink> -->
        </div>
      </transition>
    </header>

    <div class="h-16 lg:h-20"></div>

    <main class="flex-1">
      <slot />
    </main>

    <footer class="bg-gray-900 text-white border-t dark:border-gray-700">
      <div class="container mx-auto px-6 py-10 grid grid-cols-1 md:grid-cols-3 gap-8">
        <div>
          <h3 class="footer-heading">About ABAN 1 Solutions </h3>
          <p class="text-gray-300 text-sm mt-2">
            ABAN 1 Solutions is committed to providing reliable, high-quality services that help you stay compliant, ensure system performance, and protect the health and safety of your environment.
          </p>
        </div>

        <div>
          <h3 class="footer-heading">Quick Links</h3>
          <ul class="space-y-2">
            <li><NuxtLink to="/about" class="footer-link">About Us</NuxtLink></li>
            <li><NuxtLink to="/services" class="footer-link">Our Services</NuxtLink></li>
            <li><NuxtLink to="/contact" class="footer-link">Contact</NuxtLink></li>
            <li><NuxtLink to="/careers" class="footer-link">Careers</NuxtLink></li>
          </ul>
        </div>

        <div class="">
          <div class="bg-white dark:bg-gray-900 rounded-lg shadow-md space-y-4">
            <div>
              <h4 class="text-sm font-bold text-gray-900 dark:text-gray-100">📍 Reach us on:</h4>
              <p class="text-xs text-gray-600 dark:text-gray-300 mt-1">
                info@aban1solutions.com | 07703434985 | 07415103880 | 02045038409
              </p>
            </div>
            <div>
              <h4 class="text-sm font-bold text-gray-900 dark:text-gray-100">📍 Find us here:</h4>
              <p class="text-xs text-gray-600 dark:text-gray-300 mt-1">
                14 verve Apartment, 5 mercury gardens Rm1 3fb
              </p>
            </div>
          </div>
        </div>
      </div>

      <div class="border-t dark:border-gray-700 py-4 text-center text-sm text-gray-400">
        <p>&copy; 2025 ABAN 1 Solutions . All rights reserved.</p>
        <div class="flex justify-center space-x-6 mt-2">
          <NuxtLink to="/privacy" class="footer-bottom-link">Privacy Policy</NuxtLink>
          <NuxtLink to="/terms" class="footer-bottom-link">Terms of Use</NuxtLink>
          <NuxtLink to="/cookies" class="footer-bottom-link">Cookies Policy</NuxtLink>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRoute } from 'vue-router';

const menuOpen = ref(false);
const toggleMenu = () => {
  menuOpen.value = !menuOpen.value;
};

const route = useRoute();
const isActive = (path) => route.path === path;

watch(
  () => route.path,
  () => {
    menuOpen.value = false
  }
)
</script>

<style scoped>
.cta-button {
  @apply bg-red-900 rounded-md hover:bg-red-700 text-white px-6 py-3 text-sm font-semibold transition-all duration-300;
}

.h-16 {
  height: 4rem;
}
.h-20 {
  height: 5rem;
}

.nav-link {
  @apply text-gray-700 dark:text-gray-300 hover:text-red-900 transition-all duration-200 font-semibold text-sm relative;
  padding-bottom: 5px;
}

.nav-link.active {
  @apply text-red-900;
}

.nav-link.active::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -3px;
  width: 100%;
  height: 1.5px;
  transition: width 0.3s ease-in-out;
  @apply bg-red-900;
}

.dropdown-menu {
  @apply hidden absolute left-0 mt-2 bg-white shadow-lg rounded-lg w-48;
  transition: all 0.3s ease-in-out;
  z-index: 50;
}

.group:hover .dropdown-menu {
  display: block;
}

.dropdown-item {
  @apply block px-4 py-3 text-gray-700 hover:bg-red-100 transition-all;
}

.mobile-link {
  @apply block px-6 py-3 text-gray-700 border-b hover:bg-red-100 transition-all;
}

.mobile-link.active {
  @apply text-red-600 font-semibold;
  border-left: 4px solid red;
}

.icon-btn {
  @apply text-gray-700 hover:text-red-600 transition-all;
}

.slide-enter-active, .slide-leave-active {
  transition: transform 0.3s ease-in-out;
}
.slide-enter-from, .slide-leave-to {
  transform: translateY(-100%);
}

.footer-heading {
  @apply text-lg font-semibold text-gray-300 dark:text-white border-b-2 border-red-600 pb-2 text-sm mb-2;
}

.footer-link {
  @apply text-gray-300 text-xs hover:text-red-500 transition-all;
}

.social-icon {
  @apply text-gray-400 text-lg hover:text-yellow-500 transition-all;
}

.footer-bottom-link {
  @apply text-gray-400 text-xs hover:text-red-500 transition-all;
}
</style>