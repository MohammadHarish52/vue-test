<script setup>
import Hero from "@/components/Hero.vue";
import HomeCards from "@/components/HomeCards.vue";
import JobListing from "@/components/JobListing.vue";
</script>

<template>
  <Hero
    title="Become a certified dev"
    description="Find the certified job that fits your skills and needs"
  />
  <HomeCards />
  <JobListing :showButton="true" limit="3" />
</template>
