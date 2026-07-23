<template>
  <section id="pricing" class="relative py-24 sm:py-32 overflow-hidden">
    <!-- Background -->
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute top-0 left-1/2 -translate-x-1/2 w-full h-px bg-gradient-to-r from-transparent via-gray-200 dark:via-gray-800 to-transparent"></div>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center max-w-2xl mx-auto mb-16">
        <span class="inline-block px-3 py-1 text-xs font-medium text-blue-600 dark:text-blue-400 bg-blue-50 dark:bg-blue-500/10 rounded-full mb-4">Pricing</span>
        <h2 class="text-3xl sm:text-4xl font-bold tracking-tight">Transparent Starting Prices</h2>
        <p class="mt-4 text-gray-600 dark:text-gray-400 leading-relaxed">
          Every project is unique. These prices represent starting estimates. Contact us for a personalized quotation.
        </p>
      </div>

      <!-- Pricing Cards -->
      <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 max-w-5xl mx-auto">
        <!-- Starter -->
        <div class="relative group p-8 rounded-2xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900/50 hover:-translate-y-1 transition-all duration-300">
          <h3 class="text-lg font-semibold mb-1">Starter</h3>
          <p class="text-sm text-gray-500 dark:text-gray-400 mb-6">For simple websites</p>
          <div class="mb-6">
            <span class="text-4xl font-bold">$499</span>
            <span class="text-gray-500 dark:text-gray-400 text-sm ml-1">starting at</span>
          </div>
          <ul class="space-y-3 mb-8">
            <li v-for="item in starterFeatures" :key="item" class="flex items-start gap-3 text-sm text-gray-600 dark:text-gray-400">
              <svg class="w-4 h-4 text-green-500 mt-0.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
              </svg>
              {{ item }}
            </li>
          </ul>
          <a href="#contact" class="block w-full text-center px-5 py-3 text-sm font-semibold text-gray-700 dark:text-gray-300 border border-gray-300 dark:border-gray-700 rounded-full hover:bg-gray-50 dark:hover:bg-gray-800/50 transition-all duration-300">
            Request Quote
          </a>
        </div>

        <!-- Business (Featured) -->
        <div class="relative group p-8 rounded-2xl border-2 border-blue-500/30 dark:border-blue-400/30 bg-gradient-to-b from-blue-50 to-white dark:from-blue-500/5 dark:to-gray-900/50 shadow-xl shadow-blue-500/10 dark:shadow-blue-500/5 hover:-translate-y-2 transition-all duration-300 scale-105 lg:scale-110">
          <!-- Most Popular Badge -->
          <div class="absolute -top-3 left-1/2 -translate-x-1/2">
            <span class="inline-flex items-center px-3 py-1 text-xs font-semibold text-white bg-gradient-to-r from-blue-500 to-purple-600 rounded-full shadow-lg">
              Most Popular
            </span>
          </div>
          <h3 class="text-lg font-semibold mb-1">Business</h3>
          <p class="text-sm text-gray-500 dark:text-gray-400 mb-6">For growing businesses</p>
          <div class="mb-6">
            <span class="text-4xl font-bold">$999</span>
            <span class="text-gray-500 dark:text-gray-400 text-sm ml-1">starting at</span>
          </div>
          <ul class="space-y-3 mb-8">
            <li v-for="item in businessFeatures" :key="item" class="flex items-start gap-3 text-sm text-gray-600 dark:text-gray-400">
              <svg class="w-4 h-4 text-green-500 mt-0.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
              </svg>
              {{ item }}
            </li>
          </ul>
          <a href="#contact" class="block w-full text-center px-5 py-3 text-sm font-semibold text-white bg-gradient-to-r from-blue-500 to-purple-600 rounded-full shadow-lg shadow-blue-500/25 hover:shadow-xl hover:shadow-blue-500/30 transition-all duration-300">
            Request Quote
          </a>
        </div>

        <!-- Enterprise -->
        <div class="relative group p-8 rounded-2xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900/50 hover:-translate-y-1 transition-all duration-300">
          <h3 class="text-lg font-semibold mb-1">Enterprise</h3>
          <p class="text-sm text-gray-500 dark:text-gray-400 mb-6">For large-scale projects</p>
          <div class="mb-6">
            <span class="text-4xl font-bold">Custom</span>
            <span class="text-gray-500 dark:text-gray-400 text-sm ml-1">quote</span>
          </div>
          <ul class="space-y-3 mb-8">
            <li v-for="item in enterpriseFeatures" :key="item" class="flex items-start gap-3 text-sm text-gray-600 dark:text-gray-400">
              <svg class="w-4 h-4 text-green-500 mt-0.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
              </svg>
              {{ item }}
            </li>
          </ul>
          <a href="#contact" class="block w-full text-center px-5 py-3 text-sm font-semibold text-gray-700 dark:text-gray-300 border border-gray-300 dark:border-gray-700 rounded-full hover:bg-gray-50 dark:hover:bg-gray-800/50 transition-all duration-300">
            Request Quote
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const starterFeatures = [
  'Responsive Website',
  'Contact Form',
  'Basic SEO',
  'Fast Performance'
];

const businessFeatures = [
  'Custom Website',
  'CMS/Admin Dashboard',
  'Database Integration',
  'API Integration',
  'Premium UI Design'
];

const enterpriseFeatures = [
  'Enterprise Systems',
  'Mobile Applications',
  'Advanced Integrations',
  'Ongoing Support',
  'Dedicated Consultation'
];
</script>