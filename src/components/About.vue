<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true
    }
  })
  
  const element = document.getElementById('about')
  if (element) {
    observer.observe(element)
  }
})

const highlights = [
  {
    icon: '🚀',
    title: 'Lead Developer',
    description: 'Expertise in Node.js, Vue.js, AWS, PostgreSQL, and Microservices'
  },
  {
    icon: '⚡',
    title: 'Performance Optimizer',
    description: 'Passionate about building high-performance applications and optimizing system efficiency'
  },
  {
    icon: '🎯',
    title: 'Agile Advocate',
    description: 'Strong advocate of Agile methodologies, CI/CD pipelines, and TDD'
  },
  {
    icon: '👥',
    title: 'Team Leader',
    description: 'Experienced in leading cross-functional teams and mentoring developers'
  }
]
</script>

<template>
  <section id="about" class="section-padding bg-gray-900/50">
    <div class="container-custom">
      <div class="text-center mb-16" :class="{ 'animate-slide-up': isVisible }">
        <h2 class="text-4xl md:text-5xl font-bold mb-6">
          About <span class="gradient-text">Me</span>
        </h2>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto">
          A passionate developer with a decade of experience in building scalable solutions
        </p>
      </div>

      <div class="grid md:grid-cols-2 gap-12 items-center">
        <!-- Content -->
        <div :class="{ 'animate-slide-up': isVisible }" style="animation-delay: 0.2s;">
          <h3 class="text-2xl font-bold mb-6 text-blue-400">My Journey</h3>
          <p class="text-gray-300 mb-6 leading-relaxed">
            With over 10 years in the industry, I've evolved from a curious developer to a seasoned lead 
            who drives innovation and excellence. My journey spans across various technologies and domains, 
            always with a focus on creating impactful solutions.
          </p>
          <p class="text-gray-300 mb-8 leading-relaxed">
            I believe in the power of clean code, efficient architectures, and collaborative teamwork. 
            My approach combines technical expertise with strategic thinking to deliver solutions that 
            not only work but scale and adapt to future needs.
          </p>
          
          <div class="flex items-center gap-4 text-sm text-gray-400">
            <span>⚡ Fun Fact:</span>
            <span>I love traveling and playing chess! I was the lead of my school chess team.</span>
          </div>
        </div>

        <!-- Highlights Grid -->
        <div class="grid sm:grid-cols-2 gap-6" :class="{ 'animate-slide-up': isVisible }" style="animation-delay: 0.4s;">
          <div
            v-for="(highlight, index) in highlights"
            :key="index"
            class="bg-gray-800 p-6 rounded-xl card-hover border border-gray-700"
          >
            <div class="text-3xl mb-4">{{ highlight.icon }}</div>
            <h4 class="text-lg font-semibold mb-2 text-white">{{ highlight.title }}</h4>
            <p class="text-gray-400 text-sm">{{ highlight.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>