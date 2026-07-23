<template>
  <section id="portfolio" class="relative py-24 sm:py-32 overflow-hidden">
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-px bg-gradient-to-r from-transparent via-gray-200 dark:via-gray-800 to-transparent"></div>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center max-w-2xl mx-auto mb-16">
        <span class="inline-flex items-center gap-1.5 px-3 py-1 text-xs font-medium text-blue-600 dark:text-blue-400 bg-blue-50 dark:bg-blue-500/10 rounded-full mb-4">
          Portfolio
        </span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight">Selected Work</h2>
        <p class="mt-4 text-gray-600 dark:text-gray-400 leading-relaxed">
          Each project reflects our commitment to quality, performance, and thoughtful design.
        </p>
      </div>

      <!-- Project Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-6 lg:gap-8">
        <div
          v-for="(project, idx) in projects"
          :key="project.title"
          class="group relative"
        >
          <div class="relative overflow-hidden rounded-2xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900/40 transition-all duration-500 hover:shadow-2xl hover:shadow-gray-300/30 dark:hover:shadow-black/40 hover:-translate-y-1">
            <!-- Preview Image Area -->
            <div class="relative h-52 sm:h-60 overflow-hidden" :style="{ background: project.bg }">
              <!-- Subtle pattern overlay -->
              <div class="absolute inset-0 opacity-[0.03] dark:opacity-[0.05]" style="background-image: radial-gradient(circle at 2px 2px, currentColor 1px, transparent 0); background-size: 20px 20px;"></div>
              
              <!-- Floating shapes -->
              <div class="absolute inset-0 flex items-center justify-center">
                <div class="relative w-40 h-40 sm:w-48 sm:h-48">
                  <!-- Main device shape -->
                  <div class="absolute inset-0 bg-white/90 dark:bg-gray-900/90 rounded-2xl shadow-lg backdrop-blur-sm border border-gray-200/50 dark:border-gray-700/50 transition-transform duration-700 group-hover:scale-105">
                    <div class="flex items-center gap-1 px-3 py-2 border-b border-gray-100 dark:border-gray-800">
                      <div class="w-1.5 h-1.5 rounded-full bg-red-400"></div>
                      <div class="w-1.5 h-1.5 rounded-full bg-yellow-400"></div>
                      <div class="w-1.5 h-1.5 rounded-full bg-green-400"></div>
                    </div>
                    <div class="p-3 space-y-2">
                      <div class="flex items-center gap-2 mb-3">
                        <div class="w-5 h-5 rounded-md" :style="{ background: project.accent }"></div>
                        <div class="flex-1 h-1.5 rounded-full bg-gray-200 dark:bg-gray-700"></div>
                      </div>
                      <div class="grid grid-cols-3 gap-1.5">
                        <div v-for="i in 3" :key="i" class="h-8 rounded-lg" :class="project.blockColors[i-1]"></div>
                      </div>
                      <div class="flex gap-2 pt-1">
                        <div class="flex-1 h-1.5 rounded-full bg-gray-200 dark:bg-gray-700"></div>
                        <div class="flex-1 h-1.5 rounded-full bg-gray-100 dark:bg-gray-800"></div>
                      </div>
                    </div>
                  </div>
                  <!-- Floating badge -->
                  <div class="absolute -top-2 -right-2 w-8 h-8 rounded-full shadow-lg flex items-center justify-center text-white text-xs font-bold transition-transform duration-500 group-hover:scale-110" :style="{ background: project.accent }">
                    <svg class="w-3.5 h-3.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
                    </svg>
                  </div>
                </div>
              </div>

              <!-- Gradient overlays -->
              <div class="absolute inset-x-0 bottom-0 h-20 bg-gradient-to-t from-white dark:from-gray-900 to-transparent"></div>
            </div>

            <!-- Content -->
            <div class="p-5 sm:p-6">
              <div class="flex items-center justify-between mb-3">
                <span class="text-xs font-medium text-gray-500 dark:text-gray-400 tracking-wide">{{ project.category }}</span>
                <div class="flex gap-1.5">
                  <span
                    v-for="tech in project.techs"
                    :key="tech"
                    class="text-[10px] px-2 py-0.5 rounded-full font-medium bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400"
                  >
                    {{ tech }}
                  </span>
                </div>
              </div>
              <h3 class="text-lg font-semibold mb-1.5">{{ project.title }}</h3>
              <p class="text-sm text-gray-500 dark:text-gray-400 leading-relaxed mb-4">{{ project.description }}</p>
              <a
                href="#"
                class="inline-flex items-center gap-1.5 text-sm font-medium transition-colors duration-200"
                :style="{ color: project.accent }"
                @click.prevent
              >
                View Project
                <svg class="w-3.5 h-3.5 transition-transform duration-200 group-hover:translate-x-1" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- More Coming -->
      <div class="mt-16 text-center">
        <div class="inline-flex items-center gap-3 px-5 py-2.5 rounded-full bg-gray-50 dark:bg-gray-900/50 border border-gray-200 dark:border-gray-800 text-sm text-gray-500 dark:text-gray-400">
          <span class="relative flex h-2 w-2">
            <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-blue-400 opacity-75"></span>
            <span class="relative inline-flex rounded-full h-2 w-2 bg-blue-500"></span>
          </span>
          More projects coming soon
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    title: 'Velocity — Business Website',
    description: 'A performance-focused corporate landing page with fluid animations and conversion-optimized layouts.',
    category: 'Web Development',
    bg: 'linear-gradient(135deg, #eff6ff 0%, #dbeafe 50%, #bfdbfe 100%)',
    accent: '#3b82f6',
    blockColors: ['bg-blue-100 dark:bg-blue-500/20', 'bg-blue-200 dark:bg-blue-500/30', 'bg-blue-50 dark:bg-blue-500/10'],
    techs: ['Vue 3', 'Laravel', 'Tailwind']
  },
  {
    title: 'MarketFlow — E-Commerce',
    description: 'A full-featured online marketplace with custom CMS, secure payments, and real-time inventory tracking.',
    category: 'Full Stack',
    bg: 'linear-gradient(135deg, #faf5ff 0%, #f3e8ff 50%, #e9d5ff 100%)',
    accent: '#7c3aed',
    blockColors: ['bg-purple-100 dark:bg-purple-500/20', 'bg-purple-200 dark:bg-purple-500/30', 'bg-purple-50 dark:bg-purple-500/10'],
    techs: ['React', 'Node.js', 'Stripe']
  },
  {
    title: 'Pulse — Fitness App',
    description: 'A cross-platform mobile app for fitness tracking with real-time analytics, social features, and AI coaching.',
    category: 'Mobile',
    bg: 'linear-gradient(135deg, #ecfdf5 0%, #d1fae5 50%, #a7f3d0 100%)',
    accent: '#10b981',
    blockColors: ['bg-emerald-100 dark:bg-emerald-500/20', 'bg-emerald-200 dark:bg-emerald-500/30', 'bg-emerald-50 dark:bg-emerald-500/10'],
    techs: ['Flutter', 'Firebase', 'Dart']
  },
  {
    title: 'DataVista — Analytics Dashboard',
    description: 'A sophisticated analytics platform featuring real-time data visualization, custom reports, and team collaboration.',
    category: 'UI/UX',
    bg: 'linear-gradient(135deg, #fffbeb 0%, #fef3c7 50%, #fde68a 100%)',
    accent: '#f59e0b',
    blockColors: ['bg-amber-100 dark:bg-amber-500/20', 'bg-amber-200 dark:bg-amber-500/30', 'bg-amber-50 dark:bg-amber-500/10'],
    techs: ['Vue 3', 'D3.js', 'Chart.js']
  }
];
</script>