<template>
  <section id="services" class="relative py-24 sm:py-32 overflow-hidden">
    <!-- Background -->
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-px bg-gradient-to-r from-transparent via-gray-200 dark:via-gray-800 to-transparent"></div>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center max-w-2xl mx-auto mb-16">
        <span class="inline-block px-3 py-1 text-xs font-medium text-blue-600 dark:text-blue-400 bg-blue-50 dark:bg-blue-500/10 rounded-full mb-4">Services</span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight">What We Build</h2>
        <p class="mt-4 text-gray-600 dark:text-gray-400 leading-relaxed">
          From responsive websites to powerful mobile apps, we deliver end-to-end digital solutions that drive real results for your business.
        </p>
      </div>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
        <div
          v-for="(service, index) in services"
          :key="service.title"
          class="group relative p-6 sm:p-8 rounded-2xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900/50 hover:bg-gray-50 dark:hover:bg-gray-900/80 hover:shadow-xl hover:shadow-gray-200/50 dark:hover:shadow-gray-950/50 hover:-translate-y-1 transition-all duration-300"
          :style="{ animationDelay: `${0.1 + index * 0.05}s` }"
        >
          <!-- Icon -->
          <div class="w-12 h-12 rounded-xl bg-gradient-to-br from-blue-50 to-purple-50 dark:from-blue-500/10 dark:to-purple-500/10 flex items-center justify-center mb-5 group-hover:scale-110 transition-transform duration-300" v-html="service.icon"></div>
          
          <h3 class="text-lg font-semibold mb-2">{{ service.title }}</h3>
          <p class="text-sm text-gray-600 dark:text-gray-400 leading-relaxed">{{ service.description }}</p>
          
          <!-- Hover accent -->
          <div class="absolute inset-0 rounded-2xl ring-1 ring-inset ring-transparent group-hover:ring-blue-500/20 dark:group-hover:ring-blue-400/20 transition-all duration-300 pointer-events-none"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const services = [
  {
    title: 'Custom Website Development',
    description: 'Modern responsive business websites built with cutting-edge technologies for optimal performance and user experience.',
    icon: `<svg class="w-6 h-6 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M9.75 17.25v-.75a.75.75 0 01.75-.75h3a.75.75 0 01.75.75v.75m-4.5 0a.75.75 0 01-.75.75H6a.75.75 0 01-.75-.75V6a.75.75 0 01.75-.75h12A.75.75 0 0118 6v11.25a.75.75 0 01-.75.75h-3a.75.75 0 01-.75-.75m-4.5 0h4.5" />
    </svg>`
  },
  {
    title: 'Mobile App Development',
    description: 'Native and cross-platform Android & iOS apps that deliver exceptional user experiences and seamless performance.',
    icon: `<svg class="w-6 h-6 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 1.5H8.25A2.25 2.25 0 006 3.75v16.5a2.25 2.25 0 002.25 2.25h7.5A2.25 2.25 0 0018 20.25V3.75a2.25 2.25 0 00-2.25-2.25H13.5m-3 0V3h3V1.5m-3 0h3m-3 18.75h3" />
    </svg>`
  },
  {
    title: 'UI/UX Design',
    description: 'Beautiful user-centered interfaces and experiences that engage users and elevate your brand identity.',
    icon: `<svg class="w-6 h-6 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M9.53 16.122a3 3 0 00-5.78 1.128 2.25 2.25 0 01-2.4 2.245 4.5 4.5 0 008.4-2.245c0-.399-.078-.78-.22-1.128zm0 0a15.998 15.998 0 003.388-1.62m-5.043-.025a15.994 15.994 0 011.622-3.395m3.42 3.42a15.995 15.995 0 004.764-4.648l3.876-5.814a1.151 1.151 0 00-1.597-1.597L14.146 6.32a15.996 15.996 0 00-4.649 4.763m3.42 3.42a6.776 6.776 0 00-3.42-3.42" />
    </svg>`
  },
  {
    title: 'API & Backend Development',
    description: 'Secure, scalable backend systems and APIs that power your applications with reliability and speed.',
    icon: `<svg class="w-6 h-6 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M17.25 6.75L22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3l-4.5 16.5" />
    </svg>`
  },
  {
    title: 'Website Maintenance & Support',
    description: 'Continuous updates, monitoring, and improvements to keep your digital presence running smoothly and securely.',
    icon: `<svg class="w-6 h-6 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M11.42 15.17l-6.49 2.49 2.49-6.49 8.98-8.98a2.12 2.12 0 013 3l-8.98 8.98z" />
    </svg>`
  },
  {
    title: 'Cloud Hosting & Deployment',
    description: 'Fast, secure, and reliable deployment solutions on leading cloud platforms for optimal performance.',
    icon: `<svg class="w-6 h-6 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 15a4.5 4.5 0 004.5 4.5H18a3.75 3.75 0 001.332-7.257 3 3 0 00-3.758-3.848 5.25 5.25 0 00-10.233 2.33A4.502 4.502 0 002.25 15z" />
    </svg>`
  }
];
</script>