<template>
  <section id="contact" class="relative py-24 sm:py-32 overflow-hidden">
    <!-- Dark Gradient Background -->
    <div class="absolute inset-0 bg-gradient-to-br from-gray-900 via-gray-950 to-black dark:from-black dark:via-gray-950 dark:to-gray-900"></div>
    
    <!-- Glow effects -->
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute top-1/2 left-1/4 w-96 h-96 bg-blue-500/10 rounded-full blur-3xl"></div>
      <div class="absolute bottom-1/4 right-1/4 w-96 h-96 bg-purple-500/10 rounded-full blur-3xl"></div>
      <div class="absolute inset-0 bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-blue-500/5 via-transparent to-transparent"></div>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center relative z-10">
      <!-- Badge -->
      <span class="inline-block px-3 py-1 text-xs font-medium text-blue-300 bg-blue-500/10 rounded-full mb-6 backdrop-blur-sm border border-blue-500/20">
        Get In Touch
      </span>

      <h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold tracking-tight text-white max-w-3xl mx-auto">
        Let's Build Your Next Digital Product.
      </h2>
      
      <p class="mt-6 text-base sm:text-lg text-gray-300 max-w-xl mx-auto leading-relaxed">
        Whether you're launching a startup, modernizing your business, or building your next big idea, we're here to bring your vision to life.
      </p>

      <div class="mt-10 flex flex-col sm:flex-row items-center justify-center gap-4">
        <a
          href="#contact"
          class="inline-flex items-center px-6 py-3 bg-white text-gray-900 text-sm font-semibold rounded-full hover:bg-gray-100 hover:-translate-y-0.5 transition-all duration-300 shadow-xl"
        >
          Start Your Project
          <svg class="w-4 h-4 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
          </svg>
        </a>
        <a
          href="mailto:hello@martinezdigitalsolutions.com"
          class="inline-flex items-center px-6 py-3 text-sm font-semibold text-gray-300 border border-gray-700 rounded-full hover:bg-white/5 hover:border-gray-600 transition-all duration-300"
        >
          Contact Us
          <svg class="w-4 h-4 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
          </svg>
        </a>
      </div>
    </div>
  </section>
</template>