<script setup lang="ts">
import { ref, onMounted } from 'vue'

const isVisible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver((entries) => {
    if (entries[0].isIntersecting) {
      isVisible.value = true
    }
  })
  
  const element = document.getElementById('contact')
  if (element) {
    observer.observe(element)
  }
})

const contactMethods = [
  {
    icon: 'website',
    title: 'Website',
    value: 'surya-purohit.github.io',
    link: 'https://surya-purohit.github.io',
    color: 'from-blue-500 to-cyan-500'
  },
  {
    icon: 'linkedin',
    title: 'LinkedIn',
    value: 'ersuryapurohit',
    link: 'https://linkedin.com/in/ersuryapurohit',
    color: 'from-blue-600 to-blue-800'
  },
  {
    icon: 'email',
    title: 'Email',
    value: 'er.suryapurohit@gmail.com',
    link: 'mailto:er.suryapurohit@gmail.com',
    color: 'from-red-500 to-pink-500'
  }
]

const socialLinks = [
  {
    icon: 'github',
    title: 'GitHub',
    value: 'surya-purohit',
    link: 'https://github.com/surya-purohit',
    color: 'from-gray-600 to-gray-800'
  },
  {
    icon: 'stackoverflow',
    title: 'Stack Overflow',
    value: 'surya-purohit',
    link: 'https://stackoverflow.com/users/4763654/surya-purohit',
    color: 'from-orange-500 to-red-500'
  },
  {
    icon: 'twitter',
    title: 'Twitter/X',
    value: '@ErSuryaPurohit',
    link: 'https://twitter.com/ErSuryaPurohit',
    color: 'from-blue-400 to-blue-600'
  },
  {
    icon: 'facebook',
    title: 'Facebook',
    value: 'ersuryapurohit',
    link: 'https://www.facebook.com/ersuryapurohit',
    color: 'from-blue-600 to-blue-800'
  },
  {
    icon: 'instagram',
    title: 'Instagram',
    value: '@ersuryapurohit',
    link: 'https://www.instagram.com/ersuryapurohit',
    color: 'from-pink-500 to-purple-500'
  }
]

const currentYear = new Date().getFullYear()

const icons = {
  website: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-1 17.93c-3.94-.49-7-3.85-7-7.93 0-.62.08-1.21.21-1.79L9 15v1c0 1.1.9 2 2 2v1.93zm6.9-2.54c-.26-.81-1-1.39-1.9-1.39h-1v-3c0-.55-.45-1-1-1H8v-2h2c.55 0 1-.45 1-1V7h2c1.1 0 2-.9 2-2v-.41c2.93 1.19 5 4.06 5 7.41 0 2.08-.8 3.97-2.1 5.39z"/>
  </svg>`,
  linkedin: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
  </svg>`,
  email: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M20 4H4c-1.1 0-1.99.9-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V6c0-1.1-.9-2-2-2zm0 4l-8 5-8-5V6l8 5 8-5v2z"/>
  </svg>`,
  github: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
  </svg>`,
  stackoverflow: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M15.725 0l-1.72 1.277 6.39 8.588 1.716-1.277L15.725 0zm-3.94 3.418l-1.369 1.644 8.225 6.85 1.369-1.644-8.225-6.85zm-3.15 4.465l-.905 1.94 9.702 4.517.904-1.94-9.701-4.517zm-1.85 4.86l-.44 2.093 10.473 2.201.44-2.092-10.473-2.203zM1.89 15.47V24h19.19v-8.53h-2.133v6.397H4.021v-6.396H1.89zm4.265 2.133v2.13h10.66v-2.13H6.154Z"/>
  </svg>`,
  twitter: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-5.214-6.817L4.99 21.75H1.68l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/>
  </svg>`,
  facebook: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/>
  </svg>`,
  instagram: `<svg class="w-8 h-8" fill="currentColor" viewBox="0 0 24 24">
    <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
  </svg>`
}
const getIcon = (iconName: keyof typeof icons) => {
  return icons[iconName] || ''
}
</script>

<template>
  <section id="contact" class="section-padding bg-black">
    <div class="container-custom">
      <div class="text-center mb-16" :class="{ 'animate-slide-up': isVisible }">
        <h2 class="text-4xl md:text-5xl font-bold mb-6">
          Let's <span class="gradient-text">Connect</span>
        </h2>
        <p class="text-xl text-gray-400 max-w-3xl mx-auto">
          Ready to discuss your next project or just want to say hello? I'd love to hear from you!
        </p>
      </div>

      <div class="max-w-6xl mx-auto">
        <!-- Primary Contact Methods -->
        <div class="grid md:grid-cols-3 gap-8 mb-16">
          <a
            v-for="(method, index) in contactMethods"
            :key="index"
            :href="method.link"
            target="_blank"
            rel="noopener noreferrer"
            class="group bg-gray-900 p-8 rounded-xl card-hover border border-gray-700 text-center animate-slide-up"
            :class="{ 'animate-slide-up': isVisible }"
            :style="`animation-delay: ${index * 0.1}s`"
          >
            <div class="text-blue-400 mb-4 flex justify-center group-hover:scale-110 transition-transform duration-300" v-html="getIcon(method.icon as keyof typeof icons)"></div>
            <h3 class="text-xl font-bold mb-2 text-white group-hover:text-blue-400 transition-colors duration-300">
              {{ method.title }}
            </h3>
            <p class="text-gray-400 group-hover:text-gray-300 transition-colors duration-300">
              {{ method.value }}
            </p>
            <div class="mt-4 h-1 bg-gray-700 rounded-full overflow-hidden">
              <div 
                class="h-full bg-gradient-to-r w-0 group-hover:w-full transition-all duration-500"
                :class="method.color"
              ></div>
            </div>
          </a>
        </div>

        <!-- Social Media Links -->
        <div class="mb-16" :class="{ 'animate-slide-up': isVisible }" style="animation-delay: 0.3s;">
          <h3 class="text-2xl font-bold text-center mb-8 gradient-text">Follow Me</h3>
          <div class="grid grid-cols-2 md:grid-cols-5 gap-6">
            <a
              v-for="(social, index) in socialLinks"
              :key="index"
              :href="social.link"
              target="_blank"
              rel="noopener noreferrer"
              class="group bg-gray-900 p-6 rounded-xl card-hover border border-gray-700 text-center"
            >
              <div class="text-gray-400 mb-3 flex justify-center group-hover:scale-110 transition-all duration-300" 
                   :class="social.icon === 'github' ? 'group-hover:text-white' : 
                          social.icon === 'linkedin' ? 'group-hover:text-blue-500' :
                          social.icon === 'stackoverflow' ? 'group-hover:text-orange-500' :
                          social.icon === 'twitter' ? 'group-hover:text-blue-400' :
                          social.icon === 'facebook' ? 'group-hover:text-blue-600' :
                          social.icon === 'instagram' ? 'group-hover:text-pink-500' : 'group-hover:text-blue-400'"
                   v-html="getIcon(social.icon as keyof typeof icons)">
              </div>
              <h4 class="text-sm font-semibold mb-1 text-white group-hover:text-blue-400 transition-colors duration-300">
                {{ social.title }}
              </h4>
              <p class="text-xs text-gray-400 group-hover:text-gray-300 transition-colors duration-300">
                {{ social.value }}
              </p>
              <div class="mt-3 h-0.5 bg-gray-700 rounded-full overflow-hidden">
                <div 
                  class="h-full bg-gradient-to-r w-0 group-hover:w-full transition-all duration-500"
                  :class="social.color"
                ></div>
              </div>
            </a>
          </div>
        </div>

        <!-- Call to Action -->
        <div class="text-center" :class="{ 'animate-slide-up': isVisible }" style="animation-delay: 0.6s;">
          <div class="bg-gradient-to-r from-blue-900/20 to-purple-900/20 p-8 rounded-xl border border-blue-500/20">
            <h3 class="text-2xl font-bold mb-4 gradient-text">Ready to Start a Project?</h3>
            <p class="text-gray-400 mb-6 max-w-2xl mx-auto">
              Whether you're looking to build a new application, optimize existing systems, 
              or need technical leadership for your team, I'm here to help bring your vision to life.
            </p>
            <a
              href="mailto:er.suryapurohit@gmail.com"
              class="btn-primary inline-flex items-center gap-2"
            >
              <span>Send Message</span>
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"></path>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer -->
    <footer class="mt-24 pt-8 border-t border-gray-800">
      <div class="container-custom">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="text-gray-400 mb-4 md:mb-0">
            © {{ currentYear }} Surya Purohit. All rights reserved.
          </div>
          <div class="flex flex-wrap justify-center gap-4">
            <a
              href="https://surya-purohit.github.io"
              target="_blank"
              rel="noopener noreferrer"
              class="text-gray-400 hover:text-white transition-colors duration-300"
            >
              Website
            </a>
            <a
              href="https://linkedin.com/in/ersuryapurohit"
              target="_blank"
              rel="noopener noreferrer"
              class="text-gray-400 hover:text-white transition-colors duration-300"
            >
              LinkedIn
            </a>
            <a
              href="https://github.com/surya-purohit"
              target="_blank"
              rel="noopener noreferrer"
              class="text-gray-400 hover:text-white transition-colors duration-300"
            >
              GitHub
            </a>
            <a
              href="mailto:er.suryapurohit@gmail.com"
              class="text-gray-400 hover:text-white transition-colors duration-300"
            >
              Email
            </a>
          </div>
        </div>
      </div>
    </footer>
  </section>
</template>