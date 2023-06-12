<script setup lang="ts">
import NavBar from '@/components/Layout/NavBar.vue'
import HeroSection from '@/components/Home/HeroSection.vue'
import ProcessSection from '@/components/Home/ProcessSection.vue'
import WorkSection from './components/Home/WorkSection.vue';
</script>
<template>
  <NavBar></NavBar>

  <main class="mx-auto max-w-screen-2xl">
    <!-- hero section -->
    <HeroSection />
    <ProcessSection />
    <WorkSection />
  </main>
</template>
