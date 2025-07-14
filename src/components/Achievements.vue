<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true
    }
  })
  
  const element = document.getElementById('achievements')
  if (element) {
    observer.observe(element)
  }
})

const achievements = [
  {
    icon: '🏆',
    title: 'Best Project Award',
    description: 'Received recognition for exceptional work on ID Plans project',
    category: 'Recognition',
    color: 'from-yellow-500 to-orange-500'
  },
  {
    icon: '🚀',
    title: 'Early Delivery Success',
    description: 'Delivered Relay Project ahead of schedule, earning monetary rewards',
    category: 'Performance',
    color: 'from-green-500 to-emerald-500'
  },
  {
    icon: '⚡',
    title: '40% Performance Boost',
    description: 'Optimized server performance in Dopple (formerly ATLATL)',
    category: 'Optimization',
    color: 'from-blue-500 to-cyan-500'
  },
  {
    icon: '🔧',
    title: '50% Faster Deployments',
    description: 'Reduced deployment times through streamlined CI/CD processes',
    category: 'DevOps',
    color: 'from-purple-500 to-pink-500'
  },
  {
    icon: '🏗️',
    title: 'Microservices Migration',
    description: 'Spearheaded migration improving scalability by 50%',
    category: 'Architecture',
    color: 'from-indigo-500 to-purple-500'
  }
]
</script>

<template>
  <section id="achievements" class="section-padding bg-gray-900/30">
    <div class="container-custom">
      <div class="text-center mb-16" :class="{ 'animate-slide-up': isVisible }">
        <h2 class="text-4xl md:text-5xl font-bold mb-6">
          <span class="gradient-text">Achievements</span>
        </h2>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto">
          Milestones that reflect my commitment to excellence and innovation
        </p>
      </div>

      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(achievement, index) in achievements"
          :key="index"
          class="relative group"
          :class="{ 'animate-slide-up': isVisible }"
          :style="`animation-delay: ${index * 0.1}s`"
        >
          <!-- Card -->
          <div class="bg-gray-800 p-8 rounded-xl card-hover border border-gray-700 h-full relative overflow-hidden">
            <!-- Background gradient -->
            <div 
              class="absolute inset-0 bg-gradient-to-br opacity-0 group-hover:opacity-10 transition-opacity duration-300"
              :class="achievement.color"
            ></div>
            
            <div class="relative z-10">
              <!-- Icon and Category -->
              <div class="flex items-center justify-between mb-4">
                <div class="text-4xl">{{ achievement.icon }}</div>
                <span class="text-xs px-3 py-1 bg-gray-700 rounded-full text-gray-300">
                  {{ achievement.category }}
                </span>
              </div>

              <!-- Title -->
              <h3 class="text-xl font-bold mb-4 text-white group-hover:text-blue-400 transition-colors duration-300">
                {{ achievement.title }}
              </h3>

              <!-- Description -->
              <p class="text-gray-400 leading-relaxed">
                {{ achievement.description }}
              </p>

              <!-- Decorative line -->
              <div class="mt-6 h-1 bg-gray-700 rounded-full overflow-hidden">
                <div 
                  class="h-full bg-gradient-to-r w-0 group-hover:w-full transition-all duration-700 delay-300"
                  :class="achievement.color"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Summary Stats -->
      <div class="mt-16 text-center" :class="{ 'animate-slide-up': isVisible }" style="animation-delay: 0.8s;">
        <div class="bg-gray-800 p-8 rounded-xl border border-gray-700 max-w-2xl mx-auto">
          <h3 class="text-2xl font-bold mb-6 gradient-text">Impact Summary</h3>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div>
              <div class="text-3xl font-bold text-green-400 mb-2">40%</div>
              <div class="text-gray-400">Performance Improvement</div>
            </div>
            <div>
              <div class="text-3xl font-bold text-blue-400 mb-2">50%</div>
              <div class="text-gray-400">Faster Deployments</div>
            </div>
            <div>
              <div class="text-3xl font-bold text-purple-400 mb-2">50%</div>
              <div class="text-gray-400">Scalability Boost</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>