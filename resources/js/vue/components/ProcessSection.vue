<template>
  <section id="process" class="relative py-24 sm:py-32 overflow-hidden">
    <!-- Background -->
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-px bg-gradient-to-r from-transparent via-gray-200 dark:via-gray-800 to-transparent"></div>
      <div class="absolute bottom-0 left-1/2 -translate-x-1/2 w-full h-px bg-gradient-to-r from-transparent via-gray-200 dark:via-gray-800 to-transparent"></div>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center max-w-2xl mx-auto mb-16">
        <span class="inline-flex items-center gap-1.5 px-3 py-1 text-xs font-medium text-purple-600 dark:text-purple-400 bg-purple-50 dark:bg-purple-500/10 rounded-full mb-4">
          <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m0 12.75h7.5m-7.5 3H12M10.5 2.25H5.625c-.621 0-1.125.504-1.125 1.125v17.25c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9z" />
          </svg>
          Our Process
        </span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight">How We Bring Your Ideas to Life</h2>
        <p class="mt-4 text-gray-600 dark:text-gray-400 leading-relaxed max-w-xl mx-auto">
          Click through each phase to see how we transform your vision into a successful digital product.
        </p>
      </div>

      <!-- Interactive Process -->
      <div class="max-w-5xl mx-auto">
        <!-- Progress Bar -->
        <div class="mb-10">
          <div class="flex items-center justify-between mb-2">
            <span class="text-xs font-medium text-gray-500 dark:text-gray-400">Progress</span>
            <span class="text-xs font-medium text-blue-600 dark:text-blue-400">{{ Math.round(((activeStep) / (steps.length - 1)) * 100) }}%</span>
          </div>
          <div class="relative h-1.5 bg-gray-200 dark:bg-gray-800 rounded-full overflow-hidden">
            <div
              class="absolute inset-y-0 left-0 bg-gradient-to-r from-blue-500 to-purple-600 rounded-full transition-all duration-700 ease-out"
              :style="{ width: `${(activeStep / (steps.length - 1)) * 100}%` }"
            ></div>
          </div>
        </div>

        <!-- Horizontal Step Indicators -->
        <div class="hidden sm:flex items-center justify-between mb-10">
          <button
            v-for="(step, index) in steps"
            :key="step.label"
            @click="activeStep = index"
            class="relative flex flex-col items-center group focus:outline-none"
          >
            <!-- Step Circle -->
            <div
              class="relative z-10 w-10 h-10 rounded-full flex items-center justify-center transition-all duration-500 cursor-pointer"
              :class="{
                'bg-gradient-to-br from-blue-500 to-purple-600 text-white shadow-lg shadow-blue-500/25 scale-110': activeStep >= index,
                'bg-white dark:bg-gray-800 border-2 border-gray-300 dark:border-gray-600 text-gray-400 dark:text-gray-500 hover:border-blue-400 dark:hover:border-blue-500': activeStep < index
              }"
            >
              <!-- Number or check -->
              <span v-if="activeStep > index" class="text-sm font-bold">
                <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
                </svg>
              </span>
              <span v-else class="text-sm font-bold">{{ index + 1 }}</span>
            </div>
            <!-- Label -->
            <span
              class="mt-2 text-xs font-medium transition-colors duration-300 whitespace-nowrap"
              :class="activeStep === index ? 'text-blue-600 dark:text-blue-400' : 'text-gray-400 dark:text-gray-500'"
            >
              {{ step.label }}
            </span>
          </button>
        </div>

        <!-- Mobile: Step indicator dots -->
        <div class="flex sm:hidden items-center justify-center gap-2 mb-8">
          <button
            v-for="(step, index) in steps"
            :key="step.label"
            @click="activeStep = index"
            class="transition-all duration-300 focus:outline-none"
            :class="activeStep === index ? 'w-8 h-2.5 bg-blue-500 rounded-full' : 'w-2.5 h-2.5 bg-gray-300 dark:bg-gray-600 rounded-full hover:bg-gray-400 dark:hover:bg-gray-500'"
          ></button>
        </div>

        <!-- Active Step Content -->
        <transition name="step-fade" mode="out-in">
          <div :key="activeStep" class="relative">
            <div class="grid grid-cols-1 lg:grid-cols-5 gap-8 items-start">
              <!-- Left: Step Details -->
              <div class="lg:col-span-3 order-2 lg:order-1">
                <div class="p-6 sm:p-8 rounded-2xl bg-white dark:bg-gray-900/60 border border-gray-200 dark:border-gray-800 shadow-lg shadow-gray-200/30 dark:shadow-gray-950/30">
                  <!-- Step header -->
                  <div class="flex items-center gap-3 mb-5">
                    <div
                      class="w-12 h-12 rounded-xl flex items-center justify-center transition-colors duration-500"
                      :class="getIconBg(activeStep)"
                      v-html="steps[activeStep].icon"
                    ></div>
                    <div>
                      <span class="text-xs font-semibold text-gray-400 dark:text-gray-500 tracking-widest">
                        STEP {{ String(activeStep + 1).padStart(2, '0') }} / {{ String(steps.length).padStart(2, '0') }}
                      </span>
                      <h3 class="text-xl font-bold mt-0.5">{{ steps[activeStep].label }}</h3>
                    </div>
                  </div>

                  <!-- Description -->
                  <p class="text-gray-600 dark:text-gray-400 leading-relaxed mb-6">
                    {{ steps[activeStep].description }}
                  </p>

                  <!-- Detailed content per step -->
                  <div class="space-y-3">
                    <div
                      v-for="(item, i) in steps[activeStep].details"
                      :key="i"
                      class="flex items-start gap-3 text-sm"
                    >
                      <svg class="w-4 h-4 text-green-500 mt-0.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
                      </svg>
                      <span class="text-gray-600 dark:text-gray-400">{{ item }}</span>
                    </div>
                  </div>

                  <!-- Duration badge -->
                  <div class="mt-6 pt-5 border-t border-gray-100 dark:border-gray-800 flex items-center gap-2 text-sm text-gray-400 dark:text-gray-500">
                    <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
                    </svg>
                    <span>{{ steps[activeStep].duration }}</span>
                  </div>
                </div>

                <!-- Navigation Arrows -->
                <div class="flex items-center justify-between mt-6">
                  <button
                    v-if="activeStep > 0"
                    @click="activeStep--"
                    class="inline-flex items-center gap-2 px-4 py-2 text-sm font-medium text-gray-600 dark:text-gray-400 bg-white dark:bg-gray-900/60 border border-gray-200 dark:border-gray-800 rounded-full hover:shadow-md hover:-translate-x-0.5 transition-all duration-200"
                  >
                    <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18" />
                    </svg>
                    Previous: {{ steps[activeStep - 1].label }}
                  </button>
                  <div v-else></div>
                  <button
                    v-if="activeStep < steps.length - 1"
                    @click="activeStep++"
                    class="inline-flex items-center gap-2 px-5 py-2.5 text-sm font-semibold text-white bg-gradient-to-r from-blue-500 to-purple-600 rounded-full shadow-lg shadow-blue-500/20 hover:shadow-xl hover:shadow-blue-500/30 hover:translate-x-0.5 transition-all duration-200"
                  >
                    Next: {{ steps[activeStep + 1].label }}
                    <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                      <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                    </svg>
                  </button>
                </div>
              </div>

              <!-- Right: Visual Preview -->
              <div class="lg:col-span-2 order-1 lg:order-2">
                <div class="relative">
                  <!-- Main visual card -->
                  <div class="relative overflow-hidden rounded-2xl border border-gray-200 dark:border-gray-800 bg-gradient-to-br from-gray-50 to-white dark:from-gray-900 dark:to-gray-800/50 p-6 shadow-lg shadow-gray-200/30 dark:shadow-gray-950/30">
                    <!-- Animated step visualization -->
                    <div class="flex flex-col items-center text-center">
                      <!-- Large animated icon -->
                      <div
                        class="w-20 h-20 rounded-2xl flex items-center justify-center mb-4 transition-all duration-500"
                        :class="getIconBg(activeStep)"
                        v-html="steps[activeStep].largeIcon"
                      ></div>
                      <!-- Label -->
                      <h4 class="text-lg font-semibold mb-1">{{ steps[activeStep].label }}</h4>
                      <p class="text-sm text-gray-500 dark:text-gray-400 max-w-xs">{{ steps[activeStep].subtitle }}</p>
                    </div>

                    <!-- Bottom decoration -->
                    <div class="mt-6 pt-4 border-t border-gray-100 dark:border-gray-800">
                      <div class="flex items-center justify-center gap-4">
                        <div v-for="i in 3" :key="i" class="flex items-center gap-1">
                          <div
                            class="w-2 h-2 rounded-full transition-all duration-300"
                            :class="i <= Math.ceil((activeStep + 1) / 2.5) ? 'bg-blue-500' : 'bg-gray-200 dark:bg-gray-700'"
                          ></div>
                        </div>
                      </div>
                      <p class="text-xs text-gray-400 dark:text-gray-500 text-center mt-2">
                        {{ steps[activeStep].stage }} stage
                      </p>
                    </div>
                  </div>

                  <!-- Glow behind -->
                  <div class="absolute -inset-4 bg-gradient-to-br from-blue-400/10 via-transparent to-purple-400/10 dark:from-blue-400/5 dark:to-purple-400/5 rounded-3xl blur-2xl -z-10 opacity-70"></div>
                </div>
              </div>
            </div>
          </div>
        </transition>

        <!-- Bottom progress dots -->
        <div class="hidden sm:flex items-center justify-center gap-1.5 mt-10">
          <button
            v-for="(step, index) in steps"
            :key="'dot-'+index"
            @click="activeStep = index"
            class="transition-all duration-300 focus:outline-none"
            :class="activeStep === index
              ? 'w-6 h-2 bg-blue-500 rounded-full'
              : activeStep > index
                ? 'w-2 h-2 bg-blue-300 dark:bg-blue-600 rounded-full hover:bg-blue-400'
                : 'w-2 h-2 bg-gray-300 dark:bg-gray-600 rounded-full hover:bg-gray-400 dark:hover:bg-gray-500'"
          ></button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue';

const activeStep = ref(0);

const steps = [
  {
    label: 'Discovery',
    subtitle: 'Understanding your vision, goals, and market.',
    description: 'We start by diving deep into your business, goals, target audience, and competitive landscape. This foundational phase ensures every decision we make is aligned with your vision.',
    duration: '1-2 weeks',
    stage: 'Discovery',
    details: [
      'In-depth consultation and stakeholder interviews',
      'Market research and competitive analysis',
      'User persona development and journey mapping',
      'Technical feasibility assessment',
      'Project scope and requirement documentation'
    ],
    iconBg: 'bg-blue-50 dark:bg-blue-500/10 group-hover:bg-blue-100 dark:group-hover:bg-blue-500/20',
    icon: `<svg class="w-5 h-5 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
    </svg>`,
    largeIcon: `<svg class="w-9 h-9 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607zM10.5 7.5v3m0 0v3m0-3h3m-3 0H7.5" />
    </svg>`
  },
  {
    label: 'Strategy',
    subtitle: 'Mapping out a clear path to success.',
    description: 'With insights from discovery, we craft a comprehensive strategy that outlines the technical architecture, design direction, project milestones, and delivery timeline.',
    duration: '1-2 weeks',
    stage: 'Strategy',
    details: [
      'Information architecture and sitemap creation',
      'Technology stack selection and architecture design',
      'Wireframing and user flow mapping',
      'Project roadmap with milestones and deliverables',
      'Risk assessment and mitigation planning'
    ],
    iconBg: 'bg-indigo-50 dark:bg-indigo-500/10 group-hover:bg-indigo-100 dark:group-hover:bg-indigo-500/20',
    icon: `<svg class="w-5 h-5 text-indigo-600 dark:text-indigo-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6A2.25 2.25 0 016 3.75h2.25A2.25 2.25 0 0110.5 6v2.25a2.25 2.25 0 01-2.25 2.25H6a2.25 2.25 0 01-2.25-2.25V6zM3.75 15.75A2.25 2.25 0 016 13.5h2.25a2.25 2.25 0 012.25 2.25V18a2.25 2.25 0 01-2.25 2.25H6A2.25 2.25 0 013.75 18v-2.25zM13.5 6a2.25 2.25 0 012.25-2.25H18A2.25 2.25 0 0120.25 6v2.25A2.25 2.25 0 0118 10.5h-2.25a2.25 2.25 0 01-2.25-2.25V6zM13.5 15.75a2.25 2.25 0 012.25-2.25H18A2.25 2.25 0 0120.25 15.75V18A2.25 2.25 0 0118 20.25h-2.25A2.25 2.25 0 0113.5 18v-2.25z" />
    </svg>`,
    largeIcon: `<svg class="w-9 h-9 text-indigo-600 dark:text-indigo-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6A2.25 2.25 0 016 3.75h2.25A2.25 2.25 0 0110.5 6v2.25a2.25 2.25 0 01-2.25 2.25H6a2.25 2.25 0 01-2.25-2.25V6zM3.75 15.75A2.25 2.25 0 016 13.5h2.25a2.25 2.25 0 012.25 2.25V18a2.25 2.25 0 01-2.25 2.25H6A2.25 2.25 0 013.75 18v-2.25zM13.5 6a2.25 2.25 0 012.25-2.25H18A2.25 2.25 0 0120.25 6v2.25A2.25 2.25 0 0118 10.5h-2.25a2.25 2.25 0 01-2.25-2.25V6zM13.5 15.75a2.25 2.25 0 012.25-2.25H18A2.25 2.25 0 0120.25 15.75V18A2.25 2.25 0 0118 20.25h-2.25A2.25 2.25 0 0113.5 18v-2.25z" />
    </svg>`
  },
  {
    label: 'Design',
    subtitle: 'Crafting beautiful, intuitive interfaces.',
    description: 'Our designers transform strategy into stunning visual designs. We create pixel-perfect interfaces that are both beautiful and user-friendly, ensuring an exceptional experience.',
    duration: '2-3 weeks',
    stage: 'Design',
    details: [
      'UI design with modern, clean aesthetics',
      'Interactive prototype creation',
      'Client review and feedback cycles',
      'Design system and component library setup',
      'Responsive and accessibility optimization'
    ],
    iconBg: 'bg-purple-50 dark:bg-purple-500/10 group-hover:bg-purple-100 dark:group-hover:bg-purple-500/20',
    icon: `<svg class="w-5 h-5 text-purple-600 dark:text-purple-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M9.53 16.122a3 3 0 00-5.78 1.128 2.25 2.25 0 01-2.4 2.245 4.5 4.5 0 008.4-2.245c0-.399-.078-.78-.22-1.128zm0 0a15.998 15.998 0 003.388-1.62m-5.043-.025a15.994 15.994 0 011.622-3.395m3.42 3.42a15.995 15.995 0 004.764-4.648l3.876-5.814a1.151 1.151 0 00-1.597-1.597L14.146 6.32a15.996 15.996 0 00-4.649 4.763m3.42 3.42a6.776 6.776 0 00-3.42-3.42" />
    </svg>`,
    largeIcon: `<svg class="w-9 h-9 text-purple-600 dark:text-purple-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M9.53 16.122a3 3 0 00-5.78 1.128 2.25 2.25 0 01-2.4 2.245 4.5 4.5 0 008.4-2.245c0-.399-.078-.78-.22-1.128zm0 0a15.998 15.998 0 003.388-1.62m-5.043-.025a15.994 15.994 0 011.622-3.395m3.42 3.42a15.995 15.995 0 004.764-4.648l3.876-5.814a1.151 1.151 0 00-1.597-1.597L14.146 6.32a15.996 15.996 0 00-4.649 4.763m3.42 3.42a6.776 6.776 0 00-3.42-3.42" />
    </svg>`
  },
  {
    label: 'Development',
    subtitle: 'Building with clean, scalable code.',
    description: 'Our engineers bring designs to life using modern frameworks and best practices. We write clean, maintainable code and build scalable architecture that performs beautifully.',
    duration: '4-8 weeks',
    stage: 'Development',
    details: [
      'Frontend development with modern frameworks',
      'Backend API and database implementation',
      'Third-party integrations and CMS setup',
      'Performance optimization and caching',
      'Regular progress demos and milestone reviews'
    ],
    iconBg: 'bg-cyan-50 dark:bg-cyan-500/10 group-hover:bg-cyan-100 dark:group-hover:bg-cyan-500/20',
    icon: `<svg class="w-5 h-5 text-cyan-600 dark:text-cyan-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M17.25 6.75L22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3l-4.5 16.5" />
    </svg>`,
    largeIcon: `<svg class="w-9 h-9 text-cyan-600 dark:text-cyan-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M17.25 6.75L22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3l-4.5 16.5" />
    </svg>`
  },
  {
    label: 'Testing',
    subtitle: 'Ensuring quality at every level.',
    description: 'We conduct thorough testing across all devices, browsers, and scenarios to ensure your product is reliable, secure, and delivers a flawless user experience.',
    duration: '1-2 weeks',
    stage: 'Quality Assurance',
    details: [
      'Cross-browser and cross-device testing',
      'Performance and load testing',
      'Security audit and vulnerability assessment',
      'User acceptance testing (UAT)',
      'Bug tracking, fixes, and retesting'
    ],
    iconBg: 'bg-emerald-50 dark:bg-emerald-500/10 group-hover:bg-emerald-100 dark:group-hover:bg-emerald-500/20',
    icon: `<svg class="w-5 h-5 text-emerald-600 dark:text-emerald-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>`,
    largeIcon: `<svg class="w-9 h-9 text-emerald-600 dark:text-emerald-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>`
  },
  {
    label: 'Launch',
    subtitle: 'Deploying with confidence and care.',
    description: 'We handle the entire deployment process with meticulous attention, ensuring a smooth, zero-downtime launch with comprehensive monitoring and optimization.',
    duration: '1 week',
    stage: 'Launch',
    details: [
      'Production environment setup and configuration',
      'DNS migration and SSL certificate installation',
      'Automated deployment pipeline setup',
      'Performance monitoring and alert configuration',
      'Post-launch monitoring and quick fixes'
    ],
    iconBg: 'bg-orange-50 dark:bg-orange-500/10 group-hover:bg-orange-100 dark:group-hover:bg-orange-500/20',
    icon: `<svg class="w-5 h-5 text-orange-600 dark:text-orange-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M15.59 14.37a6 6 0 01-5.84 7.38v-4.8m5.84-2.58a14.98 14.98 0 006.16-12.12A14.98 14.98 0 009.631 8.41m5.96 5.96a14.926 14.926 0 01-5.841 2.58m-.119-8.54a6 6 0 00-7.381 5.84h4.8m2.581-5.84a14.927 14.927 0 00-2.58 5.84m2.699 2.7c-.103.021-.207.041-.311.06" />
    </svg>`,
    largeIcon: `<svg class="w-9 h-9 text-orange-600 dark:text-orange-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M15.59 14.37a6 6 0 01-5.84 7.38v-4.8m5.84-2.58a14.98 14.98 0 006.16-12.12A14.98 14.98 0 009.631 8.41m5.96 5.96a14.926 14.926 0 01-5.841 2.58m-.119-8.54a6 6 0 00-7.381 5.84h4.8" />
    </svg>`
  },
  {
    label: 'Support',
    subtitle: 'Ongoing partnership for long-term success.',
    description: 'Our relationship doesn\'t end at launch. We provide comprehensive ongoing support, maintenance, and continuous improvements to keep your product performing at its best.',
    duration: 'Ongoing',
    stage: 'Support',
    details: [
      '24/7 monitoring and incident response',
      'Regular updates and security patches',
      'Performance optimization and scaling',
      'Feature enhancements and iterations',
      'Dedicated account management and priority support'
    ],
    iconBg: 'bg-rose-50 dark:bg-rose-500/10 group-hover:bg-rose-100 dark:group-hover:bg-rose-500/20',
    icon: `<svg class="w-5 h-5 text-rose-600 dark:text-rose-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M18 18.72a9.094 9.094 0 003.741-.479 3 3 0 00-4.682-2.72m.94 3.198l.001.031c0 .225-.012.447-.037.666A11.944 11.944 0 0112 21c-2.17 0-4.207-.576-5.963-1.584A6.062 6.062 0 016 18.719m12 0a5.971 5.971 0 00-.941-3.197m0 0A5.995 5.995 0 0012 12.75a5.995 5.995 0 00-5.058 2.772m0 0a3 3 0 00-4.681 2.72" />
    </svg>`,
    largeIcon: `<svg class="w-9 h-9 text-rose-600 dark:text-rose-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
      <path stroke-linecap="round" stroke-linejoin="round" d="M18 18.72a9.094 9.094 0 003.741-.479 3 3 0 00-4.682-2.72m.94 3.198l.001.031c0 .225-.012.447-.037.666A11.944 11.944 0 0112 21c-2.17 0-4.207-.576-5.963-1.584A6.062 6.062 0 016 18.719m12 0a5.971 5.971 0 00-.941-3.197m0 0A5.995 5.995 0 0012 12.75" />
    </svg>`
  }
];

function getIconBg(index) {
  const bgClasses = [
    'bg-blue-50 dark:bg-blue-500/10',
    'bg-indigo-50 dark:bg-indigo-500/10',
    'bg-purple-50 dark:bg-purple-500/10',
    'bg-cyan-50 dark:bg-cyan-500/10',
    'bg-emerald-50 dark:bg-emerald-500/10',
    'bg-orange-50 dark:bg-orange-500/10',
    'bg-rose-50 dark:bg-rose-500/10'
  ];
  return bgClasses[index] || bgClasses[0];
}
</script>

<style scoped>
/* Step transition animation */
.step-fade-enter-active {
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
}
.step-fade-leave-active {
  transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
}
.step-fade-enter-from {
  opacity: 0;
  transform: translateY(20px);
}
.step-fade-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>