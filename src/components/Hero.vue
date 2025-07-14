<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

onMounted(() => {
  setTimeout(() => {
    isVisible.value = true
  }, 200)
})

const scrollToContact = () => {
  const element = document.getElementById('contact')
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const scrollToAbout = () => {
  const element = document.getElementById('about')
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}

const socialQuickLinks = [
  { 
    icon: 'github', 
    link: 'https://github.com/surya-purohit', 
    title: 'GitHub',
    color: 'hover:text-white'
  },
  { 
    icon: 'linkedin', 
    link: 'https://linkedin.com/in/ersuryapurohit', 
    title: 'LinkedIn',
    color: 'hover:text-blue-500'
  },
  { 
    icon: 'stackoverflow', 
    link: 'https://stackoverflow.com/users/4763654/surya-purohit', 
    title: 'Stack Overflow',
    color: 'hover:text-orange-500'
  },
  { 
    icon: 'twitter', 
    link: 'https://twitter.com/ErSuryaPurohit', 
    title: 'Twitter/X',
    color: 'hover:text-blue-400'
  }
]

const getIcon = (iconName: string) => {
  const icons = {
    github: `<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
      <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
    </svg>`,
    linkedin: `<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
      <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
    </svg>`,
    stackoverflow: `<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
      <path d="M15.725 0l-1.72 1.277 6.39 8.588 1.716-1.277L15.725 0zm-3.94 3.418l-1.369 1.644 8.225 6.85 1.369-1.644-8.225-6.85zm-3.15 4.465l-.905 1.94 9.702 4.517.904-1.94-9.701-4.517zm-1.85 4.86l-.44 2.093 10.473 2.201.44-2.092-10.473-2.203zM1.89 15.47V24h19.19v-8.53h-2.133v6.397H4.021v-6.396H1.89zm4.265 2.133v2.13h10.66v-2.13H6.154Z"/>
    </svg>`,
    twitter: `<svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
      <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
    </svg>`
  }
  return icons[iconName] || ''
}
</script>

<template>
  <section id="hero" class="min-h-screen flex items-center justify-center relative overflow-hidden">
    <!-- Background gradient -->
    <div class="absolute inset-0 bg-gradient-to-br from-black via-gray-900 to-black"></div>
    
    <!-- Animated background elements -->
    <div class="absolute inset-0">
      <div class="absolute top-1/4 left-1/4 w-64 h-64 bg-blue-500 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-bounce-subtle"></div>
      <div class="absolute top-3/4 right-1/4 w-64 h-64 bg-purple-500 rounded-full mix-blend-multiply filter blur-xl opacity-10 animate-bounce-subtle" style="animation-delay: 1s;"></div>
    </div>

    <div class="container-custom section-padding relative z-10">
      <div class="grid lg:grid-cols-2 gap-12 items-center" :class="{ 'animate-slide-up': isVisible }">
        <!-- Content -->
        <div class="text-center lg:text-left">
          <!-- Greeting -->
          <div class="mb-6">
            <span class="text-xl text-blue-400 font-medium">Hi there! I'm</span>
          </div>

          <!-- Name -->
          <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold mb-6">
            <span class="gradient-text">Surya Purohit</span>
          </h1>

          <!-- Title -->
          <div class="text-xl md:text-2xl lg:text-3xl text-gray-300 mb-8">
            <span class="text-blue-400">Full-Stack Lead Developer</span> | 
            <span class="text-purple-400">10+ Years Experience</span>
          </div>

          <!-- Tech Stack -->
          <div class="flex flex-wrap justify-center lg:justify-start gap-4 mb-8 text-lg">
            <span class="bg-gray-800 px-4 py-2 rounded-full text-green-400 border border-green-400/20">Node.js</span>
            <span class="bg-gray-800 px-4 py-2 rounded-full text-blue-400 border border-blue-400/20">Vue.js</span>
            <span class="bg-gray-800 px-4 py-2 rounded-full text-orange-400 border border-orange-400/20">AWS</span>
            <span class="bg-gray-800 px-4 py-2 rounded-full text-purple-400 border border-purple-400/20">PostgreSQL</span>
          </div>

          <!-- Description -->
          <p class="text-lg text-gray-400 mb-8 leading-relaxed">
            I specialize in designing and implementing scalable web applications, optimizing performance, 
            and driving projects to success. Passionate about functional programming, Agile workflows, 
            and mentoring developers.
          </p>

          <!-- Quick Social Links -->
          <div class="flex justify-center lg:justify-start gap-4 mb-8">
            <a
              v-for="(social, index) in socialQuickLinks"
              :key="index"
              :href="social.link"
              target="_blank"
              rel="noopener noreferrer"
              :title="social.title"
              class="w-12 h-12 bg-gray-800 rounded-full flex items-center justify-center text-gray-400 hover:bg-gray-700 transition-all duration-300 hover:scale-110 border border-gray-600 hover:border-blue-400"
              :class="social.color"
            >
              <div v-html="getIcon(social.icon)"></div>
            </a>
          </div>

          <!-- CTA Buttons -->
          <div class="flex flex-col sm:flex-row gap-6 justify-center lg:justify-start">
            <button @click="scrollToContact" class="btn-primary">
              Get In Touch
            </button>
            <button @click="scrollToAbout" class="btn-secondary">
              Learn More About Me
            </button>
          </div>
        </div>

        <!-- Profile Photo -->
        <div class="flex justify-center lg:justify-end">
          <div class="relative">
            <!-- Photo container with gradient border -->
            <div class="relative w-80 h-80 md:w-96 md:h-96 rounded-full p-1 bg-gradient-to-r from-blue-500 to-purple-500">
              <div class="w-full h-full rounded-full overflow-hidden bg-gray-800 flex items-center justify-center">
                <!-- Placeholder for professional photo -->
                <img 
                  src="https://images.pexels.com/photos/2379004/pexels-photo-2379004.jpeg?auto=compress&cs=tinysrgb&w=400&h=400&fit=crop"
                  alt="Surya Purohit - Full-Stack Lead Developer"
                  class="w-full h-full object-cover"
                />
              </div>
            </div>
            
            <!-- Floating elements -->
            <div class="absolute -top-4 -right-4 w-16 h-16 bg-blue-500 rounded-full flex items-center justify-center text-2xl animate-bounce-subtle">
              💻
            </div>
            <div class="absolute -bottom-4 -left-4 w-16 h-16 bg-purple-500 rounded-full flex items-center justify-center text-2xl animate-bounce-subtle" style="animation-delay: 0.5s;">
              🚀
            </div>
          </div>
        </div>
      </div>

      <!-- Arrow down -->
      <div class="mt-16 text-center animate-bounce">
        <svg class="w-6 h-6 mx-auto text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path>
        </svg>
      </div>
    </div>
  </section>
</template>