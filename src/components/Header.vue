<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

const scrollToSection = (sectionId: string) => {
  const element = document.getElementById(sectionId)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
    isMobileMenuOpen.value = false
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

const navItems = [
  { name: 'Home', id: 'hero' },
  { name: 'About', id: 'about' },
  { name: 'Skills', id: 'tech-stack' },
  { name: 'Achievements', id: 'achievements' },
  { name: 'Contact', id: 'contact' }
]
</script>

<template>
  <header 
    class="fixed w-full top-0 z-50 transition-all duration-300"
    :class="isScrolled ? 'bg-black/90 backdrop-blur-sm shadow-lg' : 'bg-transparent'"
  >
    <nav class="container-custom section-padding py-4">
      <div class="flex items-center justify-between">
        <!-- Logo -->
        <div class="text-xl font-bold gradient-text">
          Surya Purohit
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex space-x-8">
          <button
            v-for="item in navItems"
            :key="item.id"
            @click="scrollToSection(item.id)"
            class="text-gray-300 hover:text-white transition-colors duration-300 font-medium"
          >
            {{ item.name }}
          </button>
        </div>

        <!-- Mobile Menu Button -->
        <button
          class="md:hidden text-white"
          @click="isMobileMenuOpen = !isMobileMenuOpen"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path
              v-if="!isMobileMenuOpen"
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
            <path
              v-else
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>

      <!-- Mobile Navigation -->
      <div
        class="md:hidden transition-all duration-300 overflow-hidden"
        :class="isMobileMenuOpen ? 'max-h-64 mt-4' : 'max-h-0'"
      >
        <div class="py-4 space-y-4">
          <button
            v-for="item in navItems"
            :key="item.id"
            @click="scrollToSection(item.id)"
            class="block w-full text-left text-gray-300 hover:text-white transition-colors duration-300 font-medium"
          >
            {{ item.name }}
          </button>
        </div>
      </div>
    </nav>
  </header>
</template>