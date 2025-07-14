<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true
    }
  })
  
  const element = document.getElementById('tech-stack')
  if (element) {
    observer.observe(element)
  }
})

const techCategories = [
  {
    title: 'Frontend',
    icon: '🎨',
    color: 'from-blue-500 to-cyan-500',
    technologies: ['Vue.js', 'React.js', 'JavaScript', 'HTML5', 'CSS3', 'Material-UI', 'Redux', 'TypeScript']
  },
  {
    title: 'Backend',
    icon: '⚙️',
    color: 'from-green-500 to-emerald-500',
    technologies: ['Node.js', 'Express.js', 'Fastify', 'Bun', 'TypeScript', 'RESTful APIs', 'Swagger']
  },
  {
    title: 'Databases & Cache',
    icon: '🗄️',
    color: 'from-purple-500 to-pink-500',
    technologies: ['PostgreSQL', 'DynamoDB', 'Firebase', 'Redis', 'MongoDB', 'ElasticSearch']
  },
  {
    title: 'Cloud & DevOps',
    icon: '☁️',
    color: 'from-orange-500 to-red-500',
    technologies: ['AWS (S3, Lambda, SQS, SNS)', 'CI/CD', 'GitHub Actions', 'Docker', 'NewRelic']
  },
  {
    title: 'Tools & Security',
    icon: '🛠️',
    color: 'from-indigo-500 to-purple-500',
    technologies: ['JIRA', 'SonarQube', 'ESLint', 'Snyk', 'PMX', 'Agile (Scrum)', 'TDD']
  },
  {
    title: 'Payment & Real-time',
    icon: '💳',
    color: 'from-yellow-500 to-orange-500',
    technologies: ['Stripe', 'PubNub', 'WebSockets', 'Real-time APIs', 'Payment Processing']
  }
]

const featuredTech = [
  { name: 'Node.js', icon: '🟢', level: 95 },
  { name: 'Vue.js', icon: '💚', level: 90 },
  { name: 'React.js', icon: '⚛️', level: 85 },
  { name: 'AWS', icon: '☁️', level: 88 },
  { name: 'PostgreSQL', icon: '🐘', level: 85 },
  { name: 'TypeScript', icon: '📘', level: 90 }
]
</script>

<template>
  <section id="tech-stack" class="section-padding bg-black" itemScope itemType="https://schema.org/ItemList">
    <div class="container-custom">
      <div class="text-center mb-16" :class="{ 'animate-slide-up': isVisible }">
        <h2 class="text-4xl md:text-5xl font-bold mb-6" itemProp="name">
          Tech <span class="gradient-text">Stack</span>
        </h2>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto" itemProp="description">
          A comprehensive toolkit for building modern, scalable applications
        </p>
      </div>

      <!-- Featured Technologies with Progress Bars -->
      <div class="mb-16" :class="{ 'animate-slide-up': isVisible }" style="animation-delay: 0.2s;">
        <h3 class="text-2xl font-bold text-center mb-8 gradient-text" itemProp="about">Core Expertise</h3>
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
          <div
            v-for="(tech, index) in featuredTech"
            :key="index"
            class="bg-gray-900 p-6 rounded-xl border border-gray-700"
            itemScope itemType="https://schema.org/Skill"
          >
            <div class="flex items-center mb-4">
              <span class="text-2xl mr-3">{{ tech.icon }}</span>
              <h4 class="text-lg font-semibold text-white" itemProp="name">{{ tech.name }}</h4>
            </div>
            <div class="mb-2">
              <div class="flex justify-between text-sm text-gray-400 mb-1">
                <span>Proficiency</span>
                <span itemProp="proficiencyLevel">{{ tech.level }}%</span>
              </div>
              <div class="h-2 bg-gray-700 rounded-full overflow-hidden">
                <div 
                  class="h-full bg-gradient-to-r from-blue-500 to-purple-500 rounded-full transition-all duration-1000 ease-out"
                  :style="`width: ${isVisible ? tech.level : 0}%; animation-delay: ${index * 0.1}s`"
                ></div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Technology Categories -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8 mb-16">
        <div
          v-for="(category, index) in techCategories"
          :key="index"
          class="bg-gray-900 p-8 rounded-xl card-hover border border-gray-700 animate-slide-up"
          :class="{ 'animate-slide-up': isVisible }"
          :style="`animation-delay: ${index * 0.1 + 0.4}s`"
          itemScope itemType="https://schema.org/ItemList"
        >
          <!-- Header -->
          <div class="flex items-center mb-6">
            <div class="text-3xl mr-4">{{ category.icon }}</div>
            <h3 class="text-xl font-bold text-white" itemProp="name">{{ category.title }}</h3>
          </div>

          <!-- Progress bar -->
          <div class="mb-6">
            <div class="h-1 bg-gray-700 rounded-full overflow-hidden">
              <div 
                class="h-full bg-gradient-to-r rounded-full animate-fade-in"
                :class="category.color"
                style="animation-delay: 0.8s; width: 90%;"
              ></div>
            </div>
          </div>

          <!-- Technologies -->
          <div class="space-y-3">
            <div
              v-for="(tech, techIndex) in category.technologies"
              :key="techIndex"
              class="flex items-center text-gray-300 hover:text-white transition-colors duration-300"
              itemScope itemType="https://schema.org/Thing"
            >
              <div class="w-2 h-2 bg-blue-400 rounded-full mr-3"></div>
              <span itemProp="name">{{ tech }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Experience Stats -->
      <div class="grid grid-cols-2 md:grid-cols-4 gap-8" :class="{ 'animate-slide-up': isVisible }" style="animation-delay: 1s;">
        <div class="text-center">
          <div class="text-3xl font-bold gradient-text mb-2">10+</div>
          <div class="text-gray-400">Years Experience</div>
        </div>
        <div class="text-center">
          <div class="text-3xl font-bold gradient-text mb-2">50+</div>
          <div class="text-gray-400">Projects Completed</div>
        </div>
        <div class="text-center">
          <div class="text-3xl font-bold gradient-text mb-2">25+</div>
          <div class="text-gray-400">Technologies</div>
        </div>
        <div class="text-center">
          <div class="text-3xl font-bold gradient-text mb-2">5+</div>
          <div class="text-gray-400">Team Members Led</div>
        </div>
      </div>
    </div>
  </section>
</template>