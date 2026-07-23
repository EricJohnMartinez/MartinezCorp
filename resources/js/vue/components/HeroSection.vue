<template>
  <section id="home" class="relative min-h-screen flex items-center pt-20 lg:pt-0 overflow-hidden">
    <!-- Background glow effects -->
    <div class="absolute inset-0 pointer-events-none">
      <div class="absolute top-1/4 -left-32 w-96 h-96 bg-blue-500/10 dark:bg-blue-500/5 rounded-full blur-3xl"></div>
      <div class="absolute bottom-1/4 -right-32 w-96 h-96 bg-purple-500/10 dark:bg-purple-500/5 rounded-full blur-3xl"></div>
      <div class="absolute top-1/3 left-1/2 -translate-x-1/2 w-[600px] h-[600px] bg-gradient-to-br from-blue-400/5 to-purple-500/5 dark:from-blue-400/3 dark:to-purple-500/3 rounded-full blur-3xl"></div>
    </div>

    <!-- Floating particles -->
    <div class="absolute inset-0 pointer-events-none overflow-hidden">
      <div class="absolute top-20 left-[10%] w-2 h-2 bg-blue-400/30 dark:bg-blue-400/20 rounded-full animate-float-slow"></div>
      <div class="absolute top-40 left-[30%] w-1.5 h-1.5 bg-purple-400/30 dark:bg-purple-400/20 rounded-full animate-float-slower"></div>
      <div class="absolute top-60 right-[20%] w-2 h-2 bg-blue-400/20 dark:bg-blue-400/10 rounded-full animate-float"></div>
      <div class="absolute bottom-40 left-[15%] w-1 h-1 bg-purple-400/20 dark:bg-purple-400/10 rounded-full animate-float-slow"></div>
      <div class="absolute bottom-60 right-[30%] w-1.5 h-1.5 bg-blue-400/20 dark:bg-blue-400/10 rounded-full animate-float-slower"></div>
    </div>

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 w-full">
      <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-16 py-12 lg:py-20">
        <!-- Left Column -->
        <div class="flex-1 text-center lg:text-left z-10">
          <!-- Badge -->
          <div class="inline-flex items-center gap-2 px-4 py-1.5 rounded-full bg-blue-50 dark:bg-blue-500/10 border border-blue-100 dark:border-blue-500/20 mb-6 opacity-0 animate-fade-in-up" style="animation-delay: 0.1s; animation-fill-mode: forwards;">
            <span class="w-2 h-2 rounded-full bg-blue-500 animate-pulse"></span>
            <span class="text-xs font-medium text-blue-600 dark:text-blue-400">Premium Software Development Agency</span>
          </div>

          <!-- Headline -->
          <h1 class="text-4xl sm:text-5xl lg:text-6xl xl:text-7xl font-bold tracking-tight leading-tight opacity-0 animate-fade-in-up" style="animation-delay: 0.2s; animation-fill-mode: forwards;">
            We Build Modern Websites & Mobile Apps<br />
            <span class="bg-gradient-to-r from-blue-600 to-purple-600 dark:from-blue-400 dark:to-purple-400 bg-clip-text text-transparent">That Grow Your Business.</span>
          </h1>

          <!-- Subtitle -->
          <p class="mt-6 text-base sm:text-lg text-gray-600 dark:text-gray-400 max-w-lg mx-auto lg:mx-0 leading-relaxed opacity-0 animate-fade-in-up" style="animation-delay: 0.35s; animation-fill-mode: forwards;">
            We create fast, scalable, and beautifully designed websites and mobile applications tailored to your business goals. From concept to deployment, we build digital solutions that deliver exceptional user experiences and long-term value.
          </p>

          <!-- Buttons -->
          <div class="mt-8 flex flex-col sm:flex-row items-center gap-4 sm:gap-3 justify-center lg:justify-start opacity-0 animate-fade-in-up" style="animation-delay: 0.5s; animation-fill-mode: forwards;">
            <a
              href="#contact"
              class="inline-flex items-center px-6 py-3 bg-gradient-to-r from-blue-500 to-purple-600 text-white text-sm font-semibold rounded-full shadow-lg shadow-blue-500/25 dark:shadow-blue-500/20 hover:shadow-xl hover:shadow-blue-500/30 hover:-translate-y-0.5 transition-all duration-300"
            >
              Get Started
              <svg class="w-4 h-4 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
              </svg>
            </a>
            <a
              href="#portfolio"
              class="inline-flex items-center px-6 py-3 text-sm font-semibold text-gray-700 dark:text-gray-300 border border-gray-300 dark:border-gray-700 rounded-full hover:bg-gray-50 dark:hover:bg-gray-800/50 hover:border-gray-400 dark:hover:border-gray-600 transition-all duration-300"
            >
              View Portfolio
              <svg class="w-4 h-4 ml-2" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round" d="M19 9l-7 7-7-7" />
              </svg>
            </a>
          </div>

          <!-- Trust Statement -->
          <div class="mt-8 flex flex-wrap items-center gap-4 justify-center lg:justify-start opacity-0 animate-fade-in-up" style="animation-delay: 0.65s; animation-fill-mode: forwards;">
            <div class="flex -space-x-2">
              <div class="w-8 h-8 rounded-full bg-gradient-to-br from-blue-400 to-blue-600 border-2 border-white dark:border-gray-950"></div>
              <div class="w-8 h-8 rounded-full bg-gradient-to-br from-purple-400 to-purple-600 border-2 border-white dark:border-gray-950"></div>
              <div class="w-8 h-8 rounded-full bg-gradient-to-br from-pink-400 to-pink-600 border-2 border-white dark:border-gray-950"></div>
            </div>
            <span class="text-sm text-gray-500 dark:text-gray-400">
              Custom-built solutions &bull; Modern Technologies &bull; Scalable Architecture
            </span>
          </div>
        </div>

        <!-- Right Column - Illustration -->
        <div class="flex-1 relative z-10 w-full max-w-lg lg:max-w-none opacity-0 animate-fade-in-up" style="animation-delay: 0.5s; animation-fill-mode: forwards;">
          <!-- Main Mockup Cards -->
          <div class="relative">
            <!-- Laptop mockup -->
            <div class="relative bg-gradient-to-br from-gray-50 to-gray-100 dark:from-gray-900 dark:to-gray-800 rounded-2xl border border-gray-200 dark:border-gray-700 shadow-2xl shadow-gray-200/50 dark:shadow-black/50 overflow-hidden transform hover:-translate-y-1 transition-all duration-500">
              <div class="flex items-center gap-1.5 px-4 py-3 border-b border-gray-200 dark:border-gray-700 bg-gray-50/50 dark:bg-gray-900/50">
                <div class="w-2.5 h-2.5 rounded-full bg-red-400"></div>
                <div class="w-2.5 h-2.5 rounded-full bg-yellow-400"></div>
                <div class="w-2.5 h-2.5 rounded-full bg-green-400"></div>
                <div class="ml-3 text-xs text-gray-400 font-medium">martinezcorp.com</div>
              </div>
              <div class="p-4 sm:p-6">
                <div class="space-y-3">
                  <div class="flex gap-3">
                    <div class="w-8 h-8 rounded-lg bg-gradient-to-br from-blue-500 to-purple-600 flex-shrink-0"></div>
                    <div class="flex-1 space-y-2">
                      <div class="h-2.5 bg-gray-200 dark:bg-gray-700 rounded-full w-3/4"></div>
                      <div class="h-2 bg-gray-100 dark:bg-gray-800 rounded-full w-1/2"></div>
                    </div>
                  </div>
                  <div class="grid grid-cols-3 gap-2">
                    <div class="h-16 bg-gray-100 dark:bg-gray-800 rounded-lg"></div>
                    <div class="h-16 bg-blue-50 dark:bg-blue-500/10 rounded-lg"></div>
                    <div class="h-16 bg-gray-100 dark:bg-gray-800 rounded-lg"></div>
                  </div>
                  <div class="flex gap-2">
                    <div class="flex-1 h-2.5 bg-gray-200 dark:bg-gray-700 rounded-full"></div>
                    <div class="flex-1 h-2.5 bg-gray-100 dark:bg-gray-800 rounded-full"></div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Phone mockup - floating -->
            <div class="absolute -right-4 sm:right-0 -bottom-8 w-28 sm:w-32 lg:w-40 transform hover:-translate-y-2 transition-all duration-500 delay-75">
              <div class="bg-gradient-to-br from-gray-50 to-gray-100 dark:from-gray-900 dark:to-gray-800 rounded-2xl border border-gray-200 dark:border-gray-700 shadow-xl shadow-gray-200/50 dark:shadow-black/50 overflow-hidden">
                <div class="px-3 pt-3 pb-1 border-b border-gray-200 dark:border-gray-700 flex justify-center">
                  <div class="w-8 h-1 rounded-full bg-gray-300 dark:bg-gray-600"></div>
                </div>
                <div class="p-3 space-y-2">
                  <div class="flex items-center gap-2">
                    <div class="w-5 h-5 rounded bg-gradient-to-br from-blue-500 to-purple-600"></div>
                    <div class="flex-1 h-2 bg-gray-200 dark:bg-gray-700 rounded-full"></div>
                  </div>
                  <div class="h-10 bg-blue-50 dark:bg-blue-500/10 rounded-lg"></div>
                  <div class="flex gap-1">
                    <div class="flex-1 h-1.5 bg-gray-200 dark:bg-gray-700 rounded-full"></div>
                    <div class="flex-1 h-1.5 bg-gray-100 dark:bg-gray-800 rounded-full"></div>
                  </div>
                </div>
              </div>
            </div>

            <!-- Floating card -->
            <div class="absolute -left-4 top-12 w-36 sm:w-40 p-3 bg-white dark:bg-gray-800 rounded-xl border border-gray-200 dark:border-gray-700 shadow-lg shadow-gray-200/50 dark:shadow-black/50 transform hover:-translate-y-1 transition-all duration-500 delay-150 hidden sm:block">
              <div class="flex items-center gap-2 mb-2">
                <div class="w-6 h-6 rounded-full bg-green-100 dark:bg-green-500/20 flex items-center justify-center">
                  <svg class="w-3.5 h-3.5 text-green-600" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="3">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
                  </svg>
                </div>
                <span class="text-xs font-semibold">Deployed</span>
              </div>
              <div class="text-lg font-bold text-gray-900 dark:text-white">99.9%</div>
              <div class="text-xs text-gray-500">Uptime Guarantee</div>
            </div>

            <!-- Code snippet card -->
            <div class="absolute -right-2 top-4 w-32 p-2.5 bg-gray-900 dark:bg-gray-800 rounded-lg shadow-lg transform hover:-translate-y-1 transition-all duration-500 delay-100 hidden lg:block">
              <div class="flex gap-1 mb-1.5">
                <div class="w-1.5 h-1.5 rounded-full bg-red-400"></div>
                <div class="w-1.5 h-1.5 rounded-full bg-yellow-400"></div>
                <div class="w-1.5 h-1.5 rounded-full bg-green-400"></div>
              </div>
              <div class="space-y-1">
                <div class="h-1 bg-blue-400/50 rounded w-full"></div>
                <div class="h-1 bg-purple-400/50 rounded w-3/4"></div>
                <div class="h-1 bg-green-400/50 rounded w-1/2"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>