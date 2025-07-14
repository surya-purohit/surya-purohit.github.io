<script setup lang="ts">
import { ref, onMounted } from 'vue'
import Header from './components/Header.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import TechStack from './components/TechStack.vue'
import Achievements from './components/Achievements.vue'
import Contact from './components/Contact.vue'

const isLoaded = ref(false)

onMounted(() => {
  isLoaded.value = true
})
</script>

<template>
  <div class="min-h-screen bg-black text-white" :class="{ 'animate-fade-in': isLoaded }">
    <Header />
    <main>
      <Hero />
      <About />
      <TechStack />
      <Achievements />
      <Contact />
    </main>
  </div>
</template>

<style scoped>
</style>