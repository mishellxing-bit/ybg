<template>
  <div class="app">
    <Header />
    <HeroBanner />
    <PainPoints />
    <Features />
    <CTASection />
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import HeroBanner from './components/HeroBanner.vue'
import PainPoints from './components/PainPoints.vue'
import Features from './components/Features.vue'
import CTASection from './components/CTASection.vue'
import Footer from './components/Footer.vue'
</script>

<style scoped>
.app {
  min-height: 100vh;
  overflow-x: hidden;
}
</style>
