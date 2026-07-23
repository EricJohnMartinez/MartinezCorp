<template>
  <div class="min-h-screen bg-white dark:bg-gray-950 text-gray-900 dark:text-gray-100 transition-colors duration-300 font-sans overflow-x-hidden scroll-smooth">
    <NavigationBar />
    <main>
      <HeroSection />
      <ServicesSection />
      <WhyChooseUs />
      <PricingSection />
      <ProcessSection />
      <PortfolioSection />
      <CTASection />
    </main>
    <FooterSection />
  </div>
</template>

<script setup>
import NavigationBar from './NavigationBar.vue';
import HeroSection from './HeroSection.vue';
import ServicesSection from './ServicesSection.vue';
import WhyChooseUs from './WhyChooseUs.vue';
import PricingSection from './PricingSection.vue';
import ProcessSection from './ProcessSection.vue';
import PortfolioSection from './PortfolioSection.vue';
import CTASection from './CTASection.vue';
import FooterSection from './FooterSection.vue';
</script>