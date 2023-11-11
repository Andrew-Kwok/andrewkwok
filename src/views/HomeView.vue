<script setup lang="ts">
  import Navbar from '@/components/NavBar.vue'
  import HomeSection from "@/components/HomeSection.vue";
  import EducationSection from "@/components/EducationSection.vue";
  import ExperienceSection from "@/components/ExperienceSection.vue";
  import ProjectSection from "@/components/ProjectSection.vue";
  import ContactSection from "@/components/ContactSection.vue";
  import AchievementSection from "@/components/AchievementSection.vue";
</script>

<template>
  <main>
    <HomeSection />
    <Navbar />
    <EducationSection />
    <ExperienceSection />
    <AchievementSection />
    <ProjectSection />
    <ContactSection />
  </main>
</template>
