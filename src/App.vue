<script setup>
import { defineAsyncComponent } from 'vue'
import SiteHeader from './components/SiteHeader.vue'
import HeroSection from './components/HeroSection.vue'
import StatsStrip from './components/StatsStrip.vue'

const SaveSpot = defineAsyncComponent(() => import('./components/SaveSpot.vue'))
const AttendeesSection = defineAsyncComponent(() => import('./components/AttendeesSection.vue'))
const SummitTabs = defineAsyncComponent(() => import('./components/SummitTabs.vue'))
const ProgramsSection = defineAsyncComponent(() => import('./components/ProgramsSection.vue'))
const PartnersSection = defineAsyncComponent(() => import('./components/PartnersSection.vue'))
const RegisterSection = defineAsyncComponent(() => import('./components/RegisterSection.vue'))
</script>

<template>
  <SiteHeader />
  <main>
    <HeroSection />
    <StatsStrip />
    <SaveSpot />
    <AttendeesSection />
    <SummitTabs />
    <ProgramsSection />
    <PartnersSection />
    <RegisterSection />
  </main>
</template>
