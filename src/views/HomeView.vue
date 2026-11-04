<script setup lang="ts">
import AppHeader from '@/components/layout/AppHeader.vue'
import HeroSection from '@/components/sections/HeroSection.vue'
import AboutSection from '@/components/sections/AboutSection.vue'
import ServicesSection from '@/components/sections/ServicesSection.vue'
import ProjectsSection from '@/components/sections/ProjectsSection.vue'
import WhyChooseUsSection from '@/components/sections/WhyChooseUsSection.vue'
import ContactSection from '@/components/sections/ContactSection.vue'
import AppFooter from '@/components/layout/AppFooter.vue'
</script>

<template>
  <AppHeader />

  <main>
    <HeroSection />
    <AboutSection />
    <ServicesSection />
    <ProjectsSection />
    <WhyChooseUsSection />
    <ContactSection />
  </main>

  <AppFooter />
</template>
