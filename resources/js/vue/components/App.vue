<template>
  <div
    class="min-h-screen bg-white dark:bg-gray-950 text-gray-900 dark:text-gray-100 transition-colors duration-300 font-sans overflow-x-hidden scroll-smooth"
    :style="parallaxStyle"
  >
    <div class="parallax-scene" aria-hidden="true">
      <div class="parallax-layer parallax-layer-back"></div>
      <div class="parallax-layer parallax-layer-middle"></div>
      <div class="parallax-layer parallax-layer-front"></div>
    </div>
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
import { computed, onBeforeUnmount, onMounted, ref } from 'vue';
import NavigationBar from './NavigationBar.vue';
import HeroSection from './HeroSection.vue';
import ServicesSection from './ServicesSection.vue';
import WhyChooseUs from './WhyChooseUs.vue';
import PricingSection from './PricingSection.vue';
import ProcessSection from './ProcessSection.vue';
import PortfolioSection from './PortfolioSection.vue';
import CTASection from './CTASection.vue';
import FooterSection from './FooterSection.vue';

const scrollOffset = ref(0);
const pointerOffsetX = ref(0);
const pointerOffsetY = ref(0);
let animationFrame;

const parallaxStyle = computed(() => ({
  '--back-x': `${pointerOffsetX.value * 0.12}px`,
  '--back-y': `${scrollOffset.value * 0.2 + pointerOffsetY.value * 0.12}px`,
  '--middle-x': `${pointerOffsetX.value * 0.35}px`,
  '--middle-y': `${scrollOffset.value * 0.45 + pointerOffsetY.value * 0.35}px`,
  '--front-x': `${pointerOffsetX.value * 0.65}px`,
  '--front-y': `${scrollOffset.value * 0.75 + pointerOffsetY.value * 0.65}px`,
}));

const updateScrollProgress = () => {
  if (animationFrame) {
    return;
  }

  animationFrame = requestAnimationFrame(() => {
    scrollOffset.value = window.scrollY * -0.3;
    animationFrame = undefined;
  });
};

const updatePointerPosition = (event) => {
  pointerOffsetX.value = (event.clientX / window.innerWidth - 0.5) * 80;
  pointerOffsetY.value = (event.clientY / window.innerHeight - 0.5) * 50;
};

const resetPointerPosition = () => {
  pointerOffsetX.value = 0;
  pointerOffsetY.value = 0;
};

onMounted(() => {
  updateScrollProgress();
  window.addEventListener('scroll', updateScrollProgress, { passive: true });
  window.addEventListener('pointermove', updatePointerPosition, { passive: true });
  window.addEventListener('pointerleave', resetPointerPosition);
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', updateScrollProgress);
  window.removeEventListener('pointermove', updatePointerPosition);
  window.removeEventListener('pointerleave', resetPointerPosition);
  if (animationFrame) {
    cancelAnimationFrame(animationFrame);
  }
});
</script>

<style scoped>
.parallax-scene {
  position: fixed;
  inset: 0;
  z-index: 0;
  pointer-events: none;
  overflow: hidden;
  perspective: 900px;
}

.parallax-layer {
  position: absolute;
  inset: -12%;
  will-change: transform;
}

.parallax-layer-back {
  opacity: 0.35;
  background-image:
    linear-gradient(rgba(59, 130, 246, 0.14) 1px, transparent 1px),
    linear-gradient(90deg, rgba(59, 130, 246, 0.14) 1px, transparent 1px);
  background-size: 72px 72px;
  transform: translate3d(var(--back-x), var(--back-y), -80px) scale(1.1);
}

.parallax-layer-middle {
  opacity: 0.8;
  background:
    linear-gradient(115deg, transparent 18%, rgba(59, 130, 246, 0.11) 42%, transparent 62%),
    linear-gradient(295deg, transparent 28%, rgba(168, 85, 247, 0.09) 51%, transparent 72%);
  transform: translate3d(var(--middle-x), var(--middle-y), 0) scale(1.08);
}

.parallax-layer-front {
  opacity: 0.35;
  background-image: repeating-linear-gradient(135deg, transparent 0 46px, rgba(255, 255, 255, 0.2) 47px 48px, transparent 49px 96px);
  transform: translate3d(var(--front-x), var(--front-y), 80px) scale(1.06);
}

:global(main),
:global(footer) {
  position: relative;
  z-index: 1;
}

@media (prefers-reduced-motion: reduce) {
  .parallax-layer {
    transform: none;
  }
}
</style>