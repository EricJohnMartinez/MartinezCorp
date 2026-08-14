<template>
  <Teleport to="body">
    <Transition
      enter-active-class="transition ease-out duration-300"
      enter-from-class="opacity-0"
      enter-to-class="opacity-100"
      leave-active-class="transition ease-in duration-200"
      leave-from-class="opacity-100"
      leave-to-class="opacity-0"
      appear
    >
      <div
        v-if="visible"
        class="fixed inset-0 z-[100] flex items-center justify-center p-4 sm:p-6"
        @click.self="close"
      >
        <!-- Backdrop -->
        <div class="absolute inset-0 bg-gray-950/60 dark:bg-gray-950/80 backdrop-blur-sm"></div>

        <!-- Modal -->
        <div
          class="relative w-full max-w-5xl max-h-[90vh] flex flex-col bg-white dark:bg-gray-900 rounded-2xl shadow-2xl shadow-black/30 border border-gray-200 dark:border-gray-800 overflow-hidden"
          role="dialog"
          aria-modal="true"
          :aria-label="`${project.title} Preview`"
        >
          <!-- Modal Header -->
          <div class="flex items-center justify-between px-4 sm:px-6 py-3.5 border-b border-gray-200 dark:border-gray-800 bg-gray-50 dark:bg-gray-900/80 flex-shrink-0">
            <div class="flex items-center gap-3 min-w-0">
              <div class="flex items-center gap-1.5 flex-shrink-0">
                <div class="w-2.5 h-2.5 rounded-full bg-red-400"></div>
                <div class="w-2.5 h-2.5 rounded-full bg-yellow-400"></div>
                <div class="w-2.5 h-2.5 rounded-full bg-green-400"></div>
              </div>
              <div class="flex items-center gap-2 min-w-0">
                <span class="w-5 h-5 rounded-md flex items-center justify-center text-white text-[10px] font-bold flex-shrink-0" :style="{ background: project.accent }">
                  <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                    <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 6H5.25A2.25 2.25 0 003 8.25v10.5A2.25 2.25 0 005.25 21h10.5A2.25 2.25 0 0018 18.75V10.5m-10.5 6L21 3m0 0h-5.25M21 3v5.25" />
                  </svg>
                </span>
                <span class="text-xs sm:text-sm font-medium text-gray-700 dark:text-gray-300 truncate">{{ project.url }}</span>
              </div>
            </div>
            <div class="flex items-center gap-2 flex-shrink-0">
              <span class="hidden sm:inline-flex text-[10px] px-2 py-0.5 rounded-full font-medium bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400">{{ project.category }}</span>
              <button
                @click="close"
                class="w-7 h-7 rounded-full flex items-center justify-center text-gray-400 hover:text-gray-600 dark:hover:text-gray-200 hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors duration-200"
                aria-label="Close preview"
              >
                <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                </svg>
              </button>
            </div>
          </div>

          <!-- Modal Body - Scrollable -->
          <div class="flex-1 overflow-y-auto">
            <!-- Project Info Bar -->
            <div class="px-4 sm:px-6 py-4 border-b border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900">
              <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-3">
                <div class="min-w-0">
                  <h3 class="text-base sm:text-lg font-semibold text-gray-900 dark:text-white truncate">{{ project.title }}</h3>
                  <p class="text-xs sm:text-sm text-gray-500 dark:text-gray-400 mt-0.5 line-clamp-2">{{ project.description }}</p>
                </div>
                <div class="flex flex-wrap items-center gap-1.5 flex-shrink-0">
                  <span
                    v-for="tech in project.techs"
                    :key="tech"
                    class="text-[10px] px-2 py-0.5 rounded-full font-medium bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400"
                  >
                    {{ tech }}
                  </span>
                </div>
              </div>
            </div>

            <!-- Preview Area -->
            <div class="p-4 sm:p-6 bg-gray-100 dark:bg-gray-950/50">
              <!-- Velocity - Business Website Preview -->
              <div v-if="project.type === 'business'" class="rounded-xl overflow-hidden border border-gray-200 dark:border-gray-800 shadow-xl shadow-gray-300/30 dark:shadow-black/40 bg-white dark:bg-gray-900">
                <!-- Browser Chrome -->
                <div class="flex items-center gap-2 px-3 sm:px-4 py-2.5 bg-gray-100 dark:bg-gray-800 border-b border-gray-200 dark:border-gray-700">
                  <div class="flex items-center gap-1.5">
                    <div class="w-2 h-2 rounded-full bg-red-400"></div>
                    <div class="w-2 h-2 rounded-full bg-yellow-400"></div>
                    <div class="w-2 h-2 rounded-full bg-green-400"></div>
                  </div>
                  <div class="flex-1 max-w-xs mx-auto">
                    <div class="flex items-center gap-1.5 px-3 py-1 rounded-md bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-700 text-[10px] text-gray-400">
                      <svg class="w-2.5 h-2.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9 9 0 100-18 9 9 0 000 18zm0 0a9 9 0 01-9-9m9 9a9 9 0 019-9" />
                      </svg>
                      <span class="truncate">velocity.com</span>
                    </div>
                  </div>
                  <div class="w-8"></div>
                </div>

                <!-- Website Mockup -->
                <div class="bg-white dark:bg-gray-900">
                  <!-- Navbar -->
                  <div class="flex items-center justify-between px-4 sm:px-6 py-3 border-b border-gray-100 dark:border-gray-800">
                    <div class="flex items-center gap-2">
                      <div class="w-6 h-6 rounded-lg bg-gradient-to-br from-blue-500 to-purple-600 flex items-center justify-center">
                        <svg class="w-3.5 h-3.5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 6H5.25A2.25 2.25 0 003 8.25v10.5A2.25 2.25 0 005.25 21h10.5A2.25 2.25 0 0018 18.75V10.5m-10.5 6L21 3m0 0h-5.25M21 3v5.25" />
                        </svg>
                      </div>
                      <span class="text-sm font-bold text-gray-900 dark:text-white">Velocity</span>
                    </div>
                    <div class="hidden sm:flex items-center gap-4 text-[10px] font-medium text-gray-500 dark:text-gray-400">
                      <span class="text-gray-900 dark:text-white">Home</span>
                      <span>Features</span>
                      <span>Pricing</span>
                      <span>About</span>
                      <span>Contact</span>
                    </div>
                    <div class="px-3 py-1.5 rounded-full bg-gradient-to-r from-blue-500 to-purple-600 text-white text-[10px] font-semibold">Get Started</div>
                  </div>

                  <!-- Hero -->
                  <div class="relative px-4 sm:px-8 py-8 sm:py-12 text-center overflow-hidden">
                    <div class="absolute top-0 left-1/2 -translate-x-1/2 w-64 h-64 bg-blue-500/10 rounded-full blur-3xl pointer-events-none"></div>
                    <div class="relative">
                      <div class="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-full bg-blue-50 dark:bg-blue-500/10 border border-blue-100 dark:border-blue-500/20 mb-4">
                        <span class="w-1.5 h-1.5 rounded-full bg-blue-500 animate-pulse"></span>
                        <span class="text-[9px] font-medium text-blue-600 dark:text-blue-400">New: AI-powered analytics</span>
                      </div>
                      <h2 class="text-xl sm:text-2xl font-bold text-gray-900 dark:text-white tracking-tight">Grow Your Business<br />with <span class="bg-gradient-to-r from-blue-600 to-purple-600 dark:from-blue-400 dark:to-purple-400 bg-clip-text text-transparent">Velocity</span></h2>
                      <p class="mt-2 text-[10px] sm:text-xs text-gray-500 dark:text-gray-400 max-w-sm mx-auto">The all-in-one platform for modern businesses to launch, scale, and succeed online.</p>
                      <div class="mt-4 flex items-center justify-center gap-2">
                        <div class="px-3.5 py-1.5 rounded-full bg-gradient-to-r from-blue-500 to-purple-600 text-white text-[10px] font-semibold shadow-lg shadow-blue-500/25">Start Free Trial</div>
                        <div class="px-3.5 py-1.5 rounded-full border border-gray-300 dark:border-gray-700 text-gray-700 dark:text-gray-300 text-[10px] font-semibold">Watch Demo</div>
                      </div>
                    </div>
                  </div>

                  <!-- Stats -->
                  <div class="grid grid-cols-3 gap-3 px-4 sm:px-8 pb-6">
                    <div class="text-center p-3 rounded-xl bg-gray-50 dark:bg-gray-800/50 border border-gray-100 dark:border-gray-800">
                      <div class="text-base sm:text-lg font-bold text-gray-900 dark:text-white">10K+</div>
                      <div class="text-[9px] text-gray-500 dark:text-gray-400 mt-0.5">Customers</div>
                    </div>
                    <div class="text-center p-3 rounded-xl bg-gray-50 dark:bg-gray-800/50 border border-gray-100 dark:border-gray-800">
                      <div class="text-base sm:text-lg font-bold text-gray-900 dark:text-white">99.9%</div>
                      <div class="text-[9px] text-gray-500 dark:text-gray-400 mt-0.5">Uptime</div>
                    </div>
                    <div class="text-center p-3 rounded-xl bg-gray-50 dark:bg-gray-800/50 border border-gray-100 dark:border-gray-800">
                      <div class="text-base sm:text-lg font-bold text-gray-900 dark:text-white">4.9★</div>
                      <div class="text-[9px] text-gray-500 dark:text-gray-400 mt-0.5">Rating</div>
                    </div>
                  </div>

                  <!-- Features -->
                  <div class="px-4 sm:px-8 pb-6">
                    <div class="grid grid-cols-3 gap-3">
                      <div class="p-3 rounded-xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900">
                        <div class="w-7 h-7 rounded-lg bg-blue-50 dark:bg-blue-500/10 flex items-center justify-center mb-2">
                          <svg class="w-3.5 h-3.5 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M13 10V3L4 14h7v7l9-11h-7z" />
                          </svg>
                        </div>
                        <div class="text-[10px] font-semibold text-gray-900 dark:text-white">Lightning Fast</div>
                        <div class="text-[9px] text-gray-500 dark:text-gray-400 mt-0.5 leading-relaxed">Optimized for speed and performance.</div>
                      </div>
                      <div class="p-3 rounded-xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900">
                        <div class="w-7 h-7 rounded-lg bg-purple-50 dark:bg-purple-500/10 flex items-center justify-center mb-2">
                          <svg class="w-3.5 h-3.5 text-purple-600 dark:text-purple-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75m-3-7.036A11.959 11.959 0 013.598 6 11.99 11.99 0 003 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751h-.152c-3.196 0-6.1-1.248-8.25-3.285z" />
                          </svg>
                        </div>
                        <div class="text-[10px] font-semibold text-gray-900 dark:text-white">Secure</div>
                        <div class="text-[9px] text-gray-500 dark:text-gray-400 mt-0.5 leading-relaxed">Enterprise-grade security built-in.</div>
                      </div>
                      <div class="p-3 rounded-xl border border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900">
                        <div class="w-7 h-7 rounded-lg bg-emerald-50 dark:bg-emerald-500/10 flex items-center justify-center mb-2">
                          <svg class="w-3.5 h-3.5 text-emerald-600 dark:text-emerald-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 13.5l10.5-11.25L12 10.5h8.25L9.75 21.75 12 13.5H3.75z" />
                          </svg>
                        </div>
                        <div class="text-[10px] font-semibold text-gray-900 dark:text-white">Scalable</div>
                        <div class="text-[9px] text-gray-500 dark:text-gray-400 mt-0.5 leading-relaxed">Grows with your business needs.</div>
                      </div>
                    </div>
                  </div>

                  <!-- CTA + Footer -->
                  <div class="px-4 sm:px-8 pb-4">
                    <div class="rounded-xl bg-gradient-to-r from-blue-600 to-purple-600 p-4 sm:p-5 text-center">
                      <div class="text-xs sm:text-sm font-semibold text-white">Ready to accelerate your growth?</div>
                      <div class="mt-2 inline-flex px-3 py-1 rounded-full bg-white text-blue-600 text-[10px] font-semibold">Get Started Today</div>
                    </div>
                  </div>
                  <div class="px-4 sm:px-8 py-3 border-t border-gray-100 dark:border-gray-800 flex items-center justify-between">
                    <span class="text-[9px] text-gray-400">© 2026 Velocity Inc.</span>
                    <div class="flex gap-3 text-[9px] text-gray-400">
                      <span>Privacy</span>
                      <span>Terms</span>
                      <span>Support</span>
                    </div>
                  </div>
                </div>
              </div>

              <!-- MarketFlow - E-Commerce Preview -->
              <div v-else-if="project.type === 'ecommerce'" class="rounded-xl overflow-hidden border border-gray-200 dark:border-gray-800 shadow-xl shadow-gray-300/30 dark:shadow-black/40 bg-white dark:bg-gray-900">
                <!-- Browser Chrome -->
                <div class="flex items-center gap-2 px-3 sm:px-4 py-2.5 bg-gray-100 dark:bg-gray-800 border-b border-gray-200 dark:border-gray-700">
                  <div class="flex items-center gap-1.5">
                    <div class="w-2 h-2 rounded-full bg-red-400"></div>
                    <div class="w-2 h-2 rounded-full bg-yellow-400"></div>
                    <div class="w-2 h-2 rounded-full bg-green-400"></div>
                  </div>
                  <div class="flex-1 max-w-xs mx-auto">
                    <div class="flex items-center gap-1.5 px-3 py-1 rounded-md bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-700 text-[10px] text-gray-400">
                      <svg class="w-2.5 h-2.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9 9 0 100-18 9 9 0 000 18zm0 0a9 9 0 01-9-9m9 9a9 9 0 019-9" />
                      </svg>
                      <span class="truncate">marketflow.com</span>
                    </div>
                  </div>
                  <div class="w-8"></div>
                </div>

                <!-- Storefront Mockup -->
                <div class="bg-white dark:bg-gray-900">
                  <!-- Top Bar -->
                  <div class="flex items-center justify-between px-4 sm:px-6 py-3 border-b border-gray-100 dark:border-gray-800">
                    <div class="flex items-center gap-2">
                      <div class="w-6 h-6 rounded-lg bg-gradient-to-br from-purple-500 to-pink-600 flex items-center justify-center">
                        <svg class="w-3.5 h-3.5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 10.5V6a3.75 3.75 0 10-7.5 0v4.5m11.356-1.993l1.263 12c.07.665-.45 1.243-1.119 1.243H4.25a1.125 1.125 0 01-1.12-1.243l1.264-12A1.125 1.125 0 015.513 7.5h12.974c.576 0 1.059.435 1.119 1.007z" />
                        </svg>
                      </div>
                      <span class="text-sm font-bold text-gray-900 dark:text-white">MarketFlow</span>
                    </div>
                    <div class="hidden sm:flex flex-1 max-w-xs mx-4">
                      <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-gray-100 dark:bg-gray-800 text-[10px] text-gray-400 w-full">
                        <svg class="w-3 h-3 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
                        </svg>
                        <span>Search products...</span>
                      </div>
                    </div>
                    <div class="flex items-center gap-3">
                      <div class="relative">
                        <svg class="w-4 h-4 text-gray-500 dark:text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 10.5V6a3.75 3.75 0 10-7.5 0v4.5m11.356-1.993l1.263 12c.07.665-.45 1.243-1.119 1.243H4.25a1.125 1.125 0 01-1.12-1.243l1.264-12A1.125 1.125 0 015.513 7.5h12.974c.576 0 1.059.435 1.119 1.007z" />
                        </svg>
                        <span class="absolute -top-1.5 -right-1.5 w-3.5 h-3.5 rounded-full bg-purple-600 text-white text-[8px] flex items-center justify-center font-bold">3</span>
                      </div>
                      <div class="w-6 h-6 rounded-full bg-gradient-to-br from-purple-400 to-pink-500"></div>
                    </div>
                  </div>

                  <!-- Category Pills -->
                  <div class="flex items-center gap-2 px-4 sm:px-6 py-3 overflow-hidden">
                    <span class="px-2.5 py-1 rounded-full bg-purple-600 text-white text-[9px] font-semibold flex-shrink-0">All</span>
                    <span class="px-2.5 py-1 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400 text-[9px] font-medium flex-shrink-0">Electronics</span>
                    <span class="px-2.5 py-1 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400 text-[9px] font-medium flex-shrink-0">Fashion</span>
                    <span class="px-2.5 py-1 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400 text-[9px] font-medium flex-shrink-0">Home</span>
                    <span class="px-2.5 py-1 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400 text-[9px] font-medium flex-shrink-0">Sports</span>
                  </div>

                  <!-- Sale Banner -->
                  <div class="mx-4 sm:mx-6 mb-4 rounded-xl bg-gradient-to-r from-purple-600 to-pink-600 p-3 sm:p-4 flex items-center justify-between">
                    <div>
                      <div class="text-xs sm:text-sm font-bold text-white">Summer Sale — Up to 50% Off</div>
                      <div class="text-[9px] text-purple-100 mt-0.5">Limited time offer. Shop now!</div>
                    </div>
                    <div class="px-3 py-1.5 rounded-full bg-white text-purple-600 text-[9px] font-bold flex-shrink-0">Shop Now</div>
                  </div>

                  <!-- Product Grid -->
                  <div class="grid grid-cols-2 sm:grid-cols-4 gap-3 px-4 sm:px-6 pb-6">
                    <div v-for="(product, i) in products" :key="i" class="rounded-xl border border-gray-200 dark:border-gray-800 overflow-hidden bg-white dark:bg-gray-900 group">
                      <div class="relative h-20 sm:h-24" :style="{ background: product.bg }">
                        <div class="absolute inset-0 flex items-center justify-center">
                          <div class="w-10 h-10 sm:w-12 sm:h-12 rounded-xl bg-white/80 dark:bg-gray-900/80 backdrop-blur-sm flex items-center justify-center shadow-sm">
                            <span class="text-lg sm:text-xl" v-html="product.icon"></span>
                          </div>
                        </div>
                        <span class="absolute top-1.5 left-1.5 px-1.5 py-0.5 rounded-full bg-red-500 text-white text-[7px] font-bold">-{{ product.discount }}%</span>
                      </div>
                      <div class="p-2.5">
                        <div class="text-[9px] sm:text-[10px] font-medium text-gray-900 dark:text-white truncate">{{ product.name }}</div>
                        <div class="flex items-center gap-1 mt-0.5">
                          <span class="text-[8px] text-amber-400">★</span>
                          <span class="text-[8px] text-gray-400">{{ product.rating }}</span>
                        </div>
                        <div class="flex items-center justify-between mt-1.5">
                          <div>
                            <span class="text-[10px] sm:text-xs font-bold text-gray-900 dark:text-white">${{ product.price }}</span>
                            <span class="text-[8px] text-gray-400 line-through ml-1">${{ product.originalPrice }}</span>
                          </div>
                          <div class="w-5 h-5 rounded-full bg-purple-600 text-white flex items-center justify-center">
                            <svg class="w-2.5 h-2.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" />
                            </svg>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Pulse - Fitness App Preview -->
              <div v-else-if="project.type === 'mobile'" class="flex justify-center py-4">
                <!-- Phone Frame -->
                <div class="w-[280px] sm:w-[320px] rounded-[2rem] border-[6px] border-gray-900 dark:border-gray-700 bg-gray-900 dark:bg-gray-800 shadow-2xl shadow-gray-400/30 dark:shadow-black/50 overflow-hidden">
                  <!-- Notch -->
                  <div class="relative bg-gray-900 dark:bg-gray-800 pt-2 pb-1 flex justify-center">
                    <div class="w-20 h-4 rounded-full bg-gray-950 dark:bg-gray-900"></div>
                  </div>

                  <!-- App Screen -->
                  <div class="bg-gray-50 dark:bg-gray-950">
                    <!-- Status Bar -->
                    <div class="flex items-center justify-between px-4 py-1.5 text-[8px] font-semibold text-gray-900 dark:text-white">
                      <span>9:41</span>
                      <div class="flex items-center gap-1">
                        <svg class="w-2.5 h-2.5" fill="currentColor" viewBox="0 0 24 24"><path d="M2 16h20v2H2zM4 12h16v2H4zM6 8h12v2H6zM8 4h8v2H8z"/></svg>
                        <svg class="w-2.5 h-2.5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7zm0 9.5a2.5 2.5 0 010-5 2.5 2.5 0 010 5z"/></svg>
                        <svg class="w-3 h-2" fill="currentColor" viewBox="0 0 24 24"><path d="M4 7h16v10H4z" opacity="0.4"/><rect x="6" y="9" width="12" height="6" rx="1" fill="currentColor"/></svg>
                      </div>
                    </div>

                    <!-- Header -->
                    <div class="px-4 pt-2 pb-3 flex items-center justify-between">
                      <div>
                        <div class="text-[8px] text-gray-400">Good Morning</div>
                        <div class="text-sm font-bold text-gray-900 dark:text-white">Alex Martinez</div>
                      </div>
                      <div class="w-8 h-8 rounded-full bg-gradient-to-br from-emerald-400 to-teal-600 border-2 border-white dark:border-gray-900 flex items-center justify-center text-white text-[10px] font-bold">AM</div>
                    </div>

                    <!-- Activity Rings -->
                    <div class="mx-4 rounded-2xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-4 flex items-center gap-4">
                      <div class="relative w-20 h-20 flex-shrink-0">
                        <svg viewBox="0 0 80 80" class="w-20 h-20 -rotate-90">
                          <circle cx="40" cy="40" r="34" fill="none" stroke="#e5e7eb" stroke-width="6" class="dark:stroke-gray-800"/>
                          <circle cx="40" cy="40" r="34" fill="none" stroke="#10b981" stroke-width="6" stroke-linecap="round" stroke-dasharray="213.6" stroke-dashoffset="42.7"/>
                          <circle cx="40" cy="40" r="26" fill="none" stroke="#e5e7eb" stroke-width="6" class="dark:stroke-gray-800"/>
                          <circle cx="40" cy="40" r="26" fill="none" stroke="#3b82f6" stroke-width="6" stroke-linecap="round" stroke-dasharray="163.4" stroke-dashoffset="49"/>
                          <circle cx="40" cy="40" r="18" fill="none" stroke="#e5e7eb" stroke-width="6" class="dark:stroke-gray-800"/>
                          <circle cx="40" cy="40" r="18" fill="none" stroke="#f59e0b" stroke-width="6" stroke-linecap="round" stroke-dasharray="113.1" stroke-dashoffset="33.9"/>
                        </svg>
                        <div class="absolute inset-0 flex flex-col items-center justify-center">
                          <span class="text-sm font-bold text-gray-900 dark:text-white">80%</span>
                          <span class="text-[6px] text-gray-400">Daily Goal</span>
                        </div>
                      </div>
                      <div class="flex-1 space-y-2">
                        <div class="flex items-center gap-2">
                          <span class="w-2 h-2 rounded-full bg-emerald-500"></span>
                          <span class="text-[8px] text-gray-500 dark:text-gray-400 flex-1">Move</span>
                          <span class="text-[9px] font-semibold text-gray-900 dark:text-white">420/600</span>
                        </div>
                        <div class="flex items-center gap-2">
                          <span class="w-2 h-2 rounded-full bg-blue-500"></span>
                          <span class="text-[8px] text-gray-500 dark:text-gray-400 flex-1">Exercise</span>
                          <span class="text-[9px] font-semibold text-gray-900 dark:text-white">25/30 min</span>
                        </div>
                        <div class="flex items-center gap-2">
                          <span class="w-2 h-2 rounded-full bg-amber-500"></span>
                          <span class="text-[8px] text-gray-500 dark:text-gray-400 flex-1">Stand</span>
                          <span class="text-[9px] font-semibold text-gray-900 dark:text-white">8/12 hrs</span>
                        </div>
                      </div>
                    </div>

                    <!-- Stats Row -->
                    <div class="grid grid-cols-3 gap-2 px-4 py-3">
                      <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5 text-center">
                        <div class="text-sm font-bold text-gray-900 dark:text-white">8,432</div>
                        <div class="text-[7px] text-gray-400 mt-0.5">Steps</div>
                      </div>
                      <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5 text-center">
                        <div class="text-sm font-bold text-gray-900 dark:text-white">1,240</div>
                        <div class="text-[7px] text-gray-400 mt-0.5">Calories</div>
                      </div>
                      <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5 text-center">
                        <div class="text-sm font-bold text-gray-900 dark:text-white">72</div>
                        <div class="text-[7px] text-gray-400 mt-0.5">Heart Rate</div>
                      </div>
                    </div>

                    <!-- Workout List -->
                    <div class="px-4 pb-3">
                      <div class="flex items-center justify-between mb-2">
                        <span class="text-[10px] font-semibold text-gray-900 dark:text-white">Today's Workouts</span>
                        <span class="text-[8px] text-emerald-600 dark:text-emerald-400 font-medium">See All</span>
                      </div>
                      <div class="space-y-2">
                        <div class="flex items-center gap-2.5 rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5">
                          <div class="w-8 h-8 rounded-lg bg-emerald-50 dark:bg-emerald-500/10 flex items-center justify-center flex-shrink-0">
                            <svg class="w-4 h-4 text-emerald-600 dark:text-emerald-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 5.25a3 3 0 013 3m3 0a6 6 0 01-7.029 5.912c-.563-.097-1.159.026-1.563.43L10.5 17.25H8.25v2.25H6v2.25H2.25v-2.818c0-.597.237-1.17.659-1.591l6.499-6.499c.404-.404.527-1 .43-1.563A6 6 0 1121.75 8.25z" />
                            </svg>
                          </div>
                          <div class="flex-1 min-w-0">
                            <div class="text-[9px] font-semibold text-gray-900 dark:text-white">Morning Run</div>
                            <div class="text-[7px] text-gray-400">5.2 km • 32 min</div>
                          </div>
                          <span class="text-[8px] font-medium text-emerald-600 dark:text-emerald-400">Completed</span>
                        </div>
                        <div class="flex items-center gap-2.5 rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5">
                          <div class="w-8 h-8 rounded-lg bg-blue-50 dark:bg-blue-500/10 flex items-center justify-center flex-shrink-0">
                            <svg class="w-4 h-4 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
                            </svg>
                          </div>
                          <div class="flex-1 min-w-0">
                            <div class="text-[9px] font-semibold text-gray-900 dark:text-white">Strength Training</div>
                            <div class="text-[7px] text-gray-400">45 min • Full body</div>
                          </div>
                          <span class="text-[8px] font-medium text-blue-600 dark:text-blue-400">In Progress</span>
                        </div>
                        <div class="flex items-center gap-2.5 rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5">
                          <div class="w-8 h-8 rounded-lg bg-amber-50 dark:bg-amber-500/10 flex items-center justify-center flex-shrink-0">
                            <svg class="w-4 h-4 text-amber-600 dark:text-amber-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                              <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
                            </svg>
                          </div>
                          <div class="flex-1 min-w-0">
                            <div class="text-[9px] font-semibold text-gray-900 dark:text-white">Yoga Session</div>
                            <div class="text-[7px] text-gray-400">30 min • Evening</div>
                          </div>
                          <span class="text-[8px] font-medium text-gray-400">Upcoming</span>
                        </div>
                      </div>
                    </div>

                    <!-- Bottom Nav -->
                    <div class="border-t border-gray-200 dark:border-gray-800 bg-white dark:bg-gray-900 px-6 py-2.5 flex items-center justify-between">
                      <svg class="w-4 h-4 text-emerald-600 dark:text-emerald-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 12l8.954-8.955c.44-.439 1.152-.439 1.591 0L21.75 12M4.5 9.75v10.125c0 .621.504 1.125 1.125 1.125H9.75v-4.875c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21h4.125c.621 0 1.125-.504 1.125-1.125V9.75" />
                      </svg>
                      <svg class="w-4 h-4 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5" />
                      </svg>
                      <div class="w-9 h-9 -mt-5 rounded-full bg-gradient-to-br from-emerald-500 to-teal-600 border-4 border-gray-50 dark:border-gray-950 flex items-center justify-center shadow-lg">
                        <svg class="w-4 h-4 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M12 4.5v15m7.5-7.5h-15" />
                        </svg>
                      </div>
                      <svg class="w-4 h-4 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
                      </svg>
                      <svg class="w-4 h-4 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M17.982 18.725A7.488 7.488 0 0012 15.75a7.488 7.488 0 00-5.982 2.975m11.963 0a9 9 0 10-11.963 0m11.963 0A8.966 8.966 0 0112 21a8.966 8.966 0 01-5.982-2.275M15 9.75a3 3 0 11-6 0 3 3 0 016 0z" />
                      </svg>
                    </div>
                  </div>
                </div>
              </div>

              <!-- DataVista - Analytics Dashboard Preview -->
              <div v-else-if="project.type === 'dashboard'" class="rounded-xl overflow-hidden border border-gray-200 dark:border-gray-800 shadow-xl shadow-gray-300/30 dark:shadow-black/40 bg-white dark:bg-gray-900">
                <!-- Browser Chrome -->
                <div class="flex items-center gap-2 px-3 sm:px-4 py-2.5 bg-gray-100 dark:bg-gray-800 border-b border-gray-200 dark:border-gray-700">
                  <div class="flex items-center gap-1.5">
                    <div class="w-2 h-2 rounded-full bg-red-400"></div>
                    <div class="w-2 h-2 rounded-full bg-yellow-400"></div>
                    <div class="w-2 h-2 rounded-full bg-green-400"></div>
                  </div>
                  <div class="flex-1 max-w-xs mx-auto">
                    <div class="flex items-center gap-1.5 px-3 py-1 rounded-md bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-700 text-[10px] text-gray-400">
                      <svg class="w-2.5 h-2.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9 9 0 100-18 9 9 0 000 18zm0 0a9 9 0 01-9-9m9 9a9 9 0 019-9" />
                      </svg>
                      <span class="truncate">app.datavista.io</span>
                    </div>
                  </div>
                  <div class="w-8"></div>
                </div>

                <!-- Dashboard Mockup -->
                <div class="flex bg-gray-50 dark:bg-gray-950 min-h-[420px]">
                  <!-- Sidebar -->
                  <div class="w-12 sm:w-40 bg-white dark:bg-gray-900 border-r border-gray-200 dark:border-gray-800 flex-shrink-0">
                    <div class="flex items-center gap-2 px-2 sm:px-3 py-3 border-b border-gray-100 dark:border-gray-800">
                      <div class="w-6 h-6 rounded-lg bg-gradient-to-br from-amber-400 to-orange-500 flex items-center justify-center flex-shrink-0">
                        <svg class="w-3.5 h-3.5 text-white" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M3 13.125C3 12.504 3.504 12 4.125 12h2.25c.621 0 1.125.504 1.125 1.125v6.75C7.5 20.496 6.996 21 6.375 21h-2.25A1.125 1.125 0 013 19.875v-6.75zM9.75 8.625c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125v11.25c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V8.625zM16.5 4.125c0-.621.504-1.125 1.125-1.125h2.25C20.496 3 21 3.504 21 4.125v15.75c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V4.125z" />
                        </svg>
                      </div>
                      <span class="hidden sm:block text-xs font-bold text-gray-900 dark:text-white">DataVista</span>
                    </div>
                    <div class="p-2 sm:p-3 space-y-1">
                      <div class="flex items-center gap-2 px-2 py-1.5 rounded-lg bg-amber-50 dark:bg-amber-500/10 text-amber-600 dark:text-amber-400">
                        <svg class="w-3.5 h-3.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M3 13.125C3 12.504 3.504 12 4.125 12h2.25c.621 0 1.125.504 1.125 1.125v6.75C7.5 20.496 6.996 21 6.375 21h-2.25A1.125 1.125 0 013 19.875v-6.75zM9.75 8.625c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125v11.25c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V8.625zM16.5 4.125c0-.621.504-1.125 1.125-1.125h2.25C20.496 3 21 3.504 21 4.125v15.75c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V4.125z" />
                        </svg>
                        <span class="hidden sm:block text-[10px] font-medium">Dashboard</span>
                      </div>
                      <div class="flex items-center gap-2 px-2 py-1.5 rounded-lg text-gray-400 hover:bg-gray-50 dark:hover:bg-gray-800/50">
                        <svg class="w-3.5 h-3.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
                        </svg>
                        <span class="hidden sm:block text-[10px] font-medium">Analytics</span>
                      </div>
                      <div class="flex items-center gap-2 px-2 py-1.5 rounded-lg text-gray-400 hover:bg-gray-50 dark:hover:bg-gray-800/50">
                        <svg class="w-3.5 h-3.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z" />
                        </svg>
                        <span class="hidden sm:block text-[10px] font-medium">Users</span>
                      </div>
                      <div class="flex items-center gap-2 px-2 py-1.5 rounded-lg text-gray-400 hover:bg-gray-50 dark:hover:bg-gray-800/50">
                        <svg class="w-3.5 h-3.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 18L9 11.25l4.306 4.307a11.95 11.95 0 015.814-5.519l2.74-1.22m0 0l-5.94-2.28m5.94 2.28l-2.28 5.941" />
                        </svg>
                        <span class="hidden sm:block text-[10px] font-medium">Reports</span>
                      </div>
                      <div class="flex items-center gap-2 px-2 py-1.5 rounded-lg text-gray-400 hover:bg-gray-50 dark:hover:bg-gray-800/50">
                        <svg class="w-3.5 h-3.5 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                          <path stroke-linecap="round" stroke-linejoin="round" d="M10.343 3.94c.09-.542.56-.94 1.11-.94h1.093c.55 0 1.02.398 1.11.94l.149.894c.07.424.384.764.78.93.398.164.855.142 1.205-.108l.737-.527a1.125 1.125 0 011.45.12l.773.774c.39.389.44 1.002.12 1.45l-.527.737c-.25.35-.272.806-.107 1.204.165.397.505.71.93.78l.893.15c.543.09.94.56.94 1.109v1.094c0 .55-.397 1.02-.94 1.11l-.893.149c-.425.07-.765.383-.93.78-.165.398-.143.854.107 1.204l.527.738c.32.447.269 1.06-.12 1.45l-.774.773a1.125 1.125 0 01-1.449.12l-.738-.527c-.35-.25-.806-.272-1.203-.107-.397.165-.71.505-.781.929l-.149.894c-.09.542-.56.94-1.11.94h-1.094c-.55 0-1.019-.398-1.11-.94l-.148-.894c-.071-.424-.384-.764-.781-.93-.398-.164-.854-.142-1.204.108l-.738.527c-.447.32-1.06.269-1.45-.12l-.773-.774a1.125 1.125 0 01-.12-1.45l.527-.737c.25-.35.273-.806.108-1.204-.165-.397-.505-.71-.93-.78l-.894-.15c-.542-.09-.94-.56-.94-1.109v-1.094c0-.55.398-1.02.94-1.11l.894-.149c.424-.07.765-.383.93-.78.165-.398.143-.854-.108-1.204l-.526-.738a1.125 1.125 0 01.12-1.45l.773-.773a1.125 1.125 0 011.45-.12l.737.527c.35.25.807.272 1.204.107.397-.165.71-.505.78-.929l.15-.894z" />
                          <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
                        </svg>
                        <span class="hidden sm:block text-[10px] font-medium">Settings</span>
                      </div>
                    </div>
                  </div>

                  <!-- Main Content -->
                  <div class="flex-1 p-3 sm:p-4 min-w-0">
                    <!-- Top Bar -->
                    <div class="flex items-center justify-between mb-3">
                      <div>
                        <h3 class="text-xs sm:text-sm font-bold text-gray-900 dark:text-white">Analytics Overview</h3>
                        <p class="text-[8px] sm:text-[9px] text-gray-400">Real-time performance metrics</p>
                      </div>
                      <div class="flex items-center gap-2">
                        <div class="hidden sm:flex items-center gap-1.5 px-2.5 py-1 rounded-lg bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 text-[9px] text-gray-400">
                          <svg class="w-2.5 h-2.5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
                          </svg>
                          <span>Search...</span>
                        </div>
                        <div class="w-6 h-6 rounded-full bg-gradient-to-br from-amber-400 to-orange-500 flex items-center justify-center text-white text-[8px] font-bold">DV</div>
                      </div>
                    </div>

                    <!-- Stat Cards -->
                    <div class="grid grid-cols-2 sm:grid-cols-4 gap-2 mb-3">
                      <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5">
                        <div class="flex items-center justify-between mb-1">
                          <span class="text-[8px] text-gray-400">Revenue</span>
                          <span class="text-[7px] px-1 py-0.5 rounded-full bg-emerald-50 dark:bg-emerald-500/10 text-emerald-600 dark:text-emerald-400 font-medium">+12.5%</span>
                        </div>
                        <div class="text-sm sm:text-base font-bold text-gray-900 dark:text-white">$48,290</div>
                        <div class="mt-1 flex items-end gap-0.5 h-6">
                          <div class="flex-1 bg-emerald-100 dark:bg-emerald-500/20 rounded-sm" style="height: 40%"></div>
                          <div class="flex-1 bg-emerald-100 dark:bg-emerald-500/20 rounded-sm" style="height: 60%"></div>
                          <div class="flex-1 bg-emerald-100 dark:bg-emerald-500/20 rounded-sm" style="height: 45%"></div>
                          <div class="flex-1 bg-emerald-100 dark:bg-emerald-500/20 rounded-sm" style="height: 75%"></div>
                          <div class="flex-1 bg-emerald-100 dark:bg-emerald-500/20 rounded-sm" style="height: 55%"></div>
                          <div class="flex-1 bg-emerald-500 rounded-sm" style="height: 90%"></div>
                        </div>
                      </div>
                      <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5">
                        <div class="flex items-center justify-between mb-1">
                          <span class="text-[8px] text-gray-400">Users</span>
                          <span class="text-[7px] px-1 py-0.5 rounded-full bg-blue-50 dark:bg-blue-500/10 text-blue-600 dark:text-blue-400 font-medium">+8.2%</span>
                        </div>
                        <div class="text-sm sm:text-base font-bold text-gray-900 dark:text-white">12,847</div>
                        <div class="mt-1 flex items-end gap-0.5 h-6">
                          <div class="flex-1 bg-blue-100 dark:bg-blue-500/20 rounded-sm" style="height: 50%"></div>
                          <div class="flex-1 bg-blue-100 dark:bg-blue-500/20 rounded-sm" style="height: 35%"></div>
                          <div class="flex-1 bg-blue-100 dark:bg-blue-500/20 rounded-sm" style="height: 65%"></div>
                          <div class="flex-1 bg-blue-100 dark:bg-blue-500/20 rounded-sm" style="height: 45%"></div>
                          <div class="flex-1 bg-blue-100 dark:bg-blue-500/20 rounded-sm" style="height: 80%"></div>
                          <div class="flex-1 bg-blue-500 rounded-sm" style="height: 70%"></div>
                        </div>
                      </div>
                      <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5">
                        <div class="flex items-center justify-between mb-1">
                          <span class="text-[8px] text-gray-400">Conversion</span>
                          <span class="text-[7px] px-1 py-0.5 rounded-full bg-purple-50 dark:bg-purple-500/10 text-purple-600 dark:text-purple-400 font-medium">+3.1%</span>
                        </div>
                        <div class="text-sm sm:text-base font-bold text-gray-900 dark:text-white">3.42%</div>
                        <div class="mt-1 flex items-end gap-0.5 h-6">
                          <div class="flex-1 bg-purple-100 dark:bg-purple-500/20 rounded-sm" style="height: 30%"></div>
                          <div class="flex-1 bg-purple-100 dark:bg-purple-500/20 rounded-sm" style="height: 55%"></div>
                          <div class="flex-1 bg-purple-100 dark:bg-purple-500/20 rounded-sm" style="height: 40%"></div>
                          <div class="flex-1 bg-purple-100 dark:bg-purple-500/20 rounded-sm" style="height: 70%"></div>
                          <div class="flex-1 bg-purple-100 dark:bg-purple-500/20 rounded-sm" style="height: 50%"></div>
                          <div class="flex-1 bg-purple-500 rounded-sm" style="height: 85%"></div>
                        </div>
                      </div>
                      <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2.5">
                        <div class="flex items-center justify-between mb-1">
                          <span class="text-[8px] text-gray-400">Avg. Session</span>
                          <span class="text-[7px] px-1 py-0.5 rounded-full bg-amber-50 dark:bg-amber-500/10 text-amber-600 dark:text-amber-400 font-medium">-1.4%</span>
                        </div>
                        <div class="text-sm sm:text-base font-bold text-gray-900 dark:text-white">4m 32s</div>
                        <div class="mt-1 flex items-end gap-0.5 h-6">
                          <div class="flex-1 bg-amber-100 dark:bg-amber-500/20 rounded-sm" style="height: 60%"></div>
                          <div class="flex-1 bg-amber-100 dark:bg-amber-500/20 rounded-sm" style="height: 45%"></div>
                          <div class="flex-1 bg-amber-100 dark:bg-amber-500/20 rounded-sm" style="height: 70%"></div>
                          <div class="flex-1 bg-amber-100 dark:bg-amber-500/20 rounded-sm" style="height: 50%"></div>
                          <div class="flex-1 bg-amber-100 dark:bg-amber-500/20 rounded-sm" style="height: 65%"></div>
                          <div class="flex-1 bg-amber-500 rounded-sm" style="height: 55%"></div>
                        </div>
                      </div>
                    </div>

                    <!-- Charts Row -->
                    <div class="grid grid-cols-1 sm:grid-cols-5 gap-2 mb-3">
                      <!-- Bar Chart -->
                      <div class="sm:col-span-3 rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-3">
                        <div class="flex items-center justify-between mb-3">
                          <span class="text-[9px] font-semibold text-gray-900 dark:text-white">Monthly Revenue</span>
                          <div class="flex items-center gap-1.5">
                            <span class="text-[7px] px-1.5 py-0.5 rounded-full bg-gray-100 dark:bg-gray-800 text-gray-500 dark:text-gray-400 font-medium">Last 6 months</span>
                          </div>
                        </div>
                        <div class="flex items-end justify-between gap-1.5 h-24">
                          <div v-for="(bar, i) in revenueBars" :key="i" class="flex-1 flex flex-col items-center gap-1">
                            <div class="w-full rounded-t-md bg-gradient-to-t from-amber-500/80 to-amber-400" :style="{ height: bar + '%' }"></div>
                            <span class="text-[6px] text-gray-400">{{ barLabels[i] }}</span>
                          </div>
                        </div>
                      </div>

                      <!-- Line Chart -->
                      <div class="sm:col-span-2 rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-3">
                        <div class="flex items-center justify-between mb-3">
                          <span class="text-[9px] font-semibold text-gray-900 dark:text-white">Traffic Sources</span>
                        </div>
                        <div class="space-y-2">
                          <div v-for="(source, i) in trafficSources" :key="i" class="flex items-center gap-2">
                            <span class="w-1.5 h-1.5 rounded-full flex-shrink-0" :style="{ background: source.color }"></span>
                            <span class="text-[8px] text-gray-500 dark:text-gray-400 flex-1">{{ source.name }}</span>
                            <span class="text-[8px] font-semibold text-gray-900 dark:text-white">{{ source.value }}%</span>
                            <div class="w-12 h-1 rounded-full bg-gray-100 dark:bg-gray-800 overflow-hidden">
                              <div class="h-full rounded-full" :style="{ width: source.value + '%', background: source.color }"></div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>

                    <!-- Recent Activity Table -->
                    <div class="rounded-xl bg-white dark:bg-gray-900 border border-gray-200 dark:border-gray-800 overflow-hidden">
                      <div class="px-3 py-2.5 border-b border-gray-100 dark:border-gray-800">
                        <span class="text-[9px] font-semibold text-gray-900 dark:text-white">Recent Activity</span>
                      </div>
                      <div class="overflow-x-auto">
                        <table class="w-full text-left">
                          <thead>
                            <tr class="border-b border-gray-100 dark:border-gray-800">
                              <th class="px-3 py-1.5 text-[7px] font-medium text-gray-400 uppercase">User</th>
                              <th class="px-3 py-1.5 text-[7px] font-medium text-gray-400 uppercase">Action</th>
                              <th class="px-3 py-1.5 text-[7px] font-medium text-gray-400 uppercase">Status</th>
                              <th class="px-3 py-1.5 text-[7px] font-medium text-gray-400 uppercase">Time</th>
                            </tr>
                          </thead>
                          <tbody>
                            <tr v-for="(row, i) in activityRows" :key="i" class="border-b border-gray-50 dark:border-gray-800/50 last:border-0">
                              <td class="px-3 py-2">
                                <div class="flex items-center gap-1.5">
                                  <div class="w-4 h-4 rounded-full flex-shrink-0" :style="{ background: row.avatarBg }"></div>
                                  <span class="text-[8px] font-medium text-gray-900 dark:text-white whitespace-nowrap">{{ row.user }}</span>
                                </div>
                              </td>
                              <td class="px-3 py-2 text-[8px] text-gray-500 dark:text-gray-400 whitespace-nowrap">{{ row.action }}</td>
                              <td class="px-3 py-2">
                                <span class="text-[7px] px-1.5 py-0.5 rounded-full font-medium whitespace-nowrap" :class="row.statusClass">{{ row.status }}</span>
                              </td>
                              <td class="px-3 py-2 text-[8px] text-gray-400 whitespace-nowrap">{{ row.time }}</td>
                            </tr>
                          </tbody>
                        </table>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </Transition>
  </Teleport>
</template>

<script setup>
import { ref, watch, onMounted, onBeforeUnmount } from 'vue';

const props = defineProps({
  project: {
    type: Object,
    required: true
  },
  visible: {
    type: Boolean,
    default: false
  }
});

const emit = defineEmits(['close']);

const visible = ref(props.visible);

watch(() => props.visible, (val) => {
  visible.value = val;
  if (val) {
    document.body.style.overflow = 'hidden';
  } else {
    document.body.style.overflow = '';
  }
});

function close() {
  emit('close');
}

function handleKeydown(e) {
  if (e.key === 'Escape' && visible.value) {
    close();
  }
}

onMounted(() => {
  window.addEventListener('keydown', handleKeydown);
});

onBeforeUnmount(() => {
  window.removeEventListener('keydown', handleKeydown);
  document.body.style.overflow = '';
});

// E-commerce products data
const products = [
  {
    name: 'Wireless Headphones',
    price: '89.99',
    originalPrice: '149.99',
    rating: '4.8',
    discount: '40',
    bg: 'linear-gradient(135deg, #f3e8ff 0%, #e9d5ff 100%)',
    icon: '<span>🎧</span>'
  },
  {
    name: 'Smart Watch Series 7',
    price: '199.99',
    originalPrice: '299.99',
    rating: '4.9',
    discount: '33',
    bg: 'linear-gradient(135deg, #dbeafe 0%, #bfdbfe 100%)',
    icon: '<span>⌚</span>'
  },
  {
    name: 'Premium Sneakers',
    price: '74.99',
    originalPrice: '129.99',
    rating: '4.7',
    discount: '42',
    bg: 'linear-gradient(135deg, #fef3c7 0%, #fde68a 100%)',
    icon: '<span>👟</span>'
  },
  {
    name: 'Mechanical Keyboard',
    price: '119.99',
    originalPrice: '179.99',
    rating: '4.6',
    discount: '33',
    bg: 'linear-gradient(135deg, #d1fae5 0%, #a7f3d0 100%)',
    icon: '<span>⌨️</span>'
  }
];

// Dashboard data
const revenueBars = [45, 65, 50, 80, 60, 95];
const barLabels = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'];

const trafficSources = [
  { name: 'Organic Search', value: 45, color: '#f59e0b' },
  { name: 'Direct', value: 25, color: '#3b82f6' },
  { name: 'Referral', value: 18, color: '#10b981' },
  { name: 'Social', value: 12, color: '#8b5cf6' }
];

const activityRows = [
  {
    user: 'Sarah Chen',
    action: 'Completed purchase #2841',
    status: 'Completed',
    statusClass: 'bg-emerald-50 dark:bg-emerald-500/10 text-emerald-600 dark:text-emerald-400',
    time: '2 min ago',
    avatarBg: 'linear-gradient(135deg, #f472b6, #ec4899)'
  },
  {
    user: 'Mike Johnson',
    action: 'Signed up for Pro plan',
    status: 'Completed',
    statusClass: 'bg-emerald-50 dark:bg-emerald-500/10 text-emerald-600 dark:text-emerald-400',
    time: '15 min ago',
    avatarBg: 'linear-gradient(135deg, #60a5fa, #3b82f6)'
  },
  {
    user: 'Emily Rodriguez',
    action: 'Updated profile settings',
    status: 'Pending',
    statusClass: 'bg-amber-50 dark:bg-amber-500/10 text-amber-600 dark:text-amber-400',
    time: '28 min ago',
    avatarBg: 'linear-gradient(135deg, #fbbf24, #f59e0b)'
  },
  {
    user: 'David Kim',
    action: 'Exported monthly report',
    status: 'Completed',
    statusClass: 'bg-emerald-50 dark:bg-emerald-500/10 text-emerald-600 dark:text-emerald-400',
    time: '1 hr ago',
    avatarBg: 'linear-gradient(135deg, #34d399, #10b981)'
  }
];
</script>