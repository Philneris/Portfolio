<template>
  <div id="portfolio">
    <NavBar />
    <HeroSection />
    <AboutSection />
    <ServicesSection />
    <ExperienceSection />
    <ProjectsSection />
    <TestimonialsSection />
    <ContactSection />
    <FooterSection />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<style>
#portfolio {
  min-height: 100vh;
}
</style>
