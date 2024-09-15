<script setup>
import { ref, defineProps } from "vue";
import JobListingCard from "./JobListingCard.vue";
import jobsData from "@/jobs.json";

// Create a ref for the job listings
const jobListings = ref(jobsData);

defineProps({
  limit: {
    type: Number,
    default: 3,
  },
  showButton: {
    type: Boolean,
    default: false,
  },
});

// Add this function to handle company data
const getCompanyName = (company) => {
  return typeof company === "object" ? company.name : company;
};
</script>

<template>
  <section class="bg-purple-50 px-4 py-10">
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-purple-500 mb-6 text-center">
        Browse Jobs
      </h2>
      <p>Debug: {{ jobListings.length }} jobs available</p>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <JobListingCard
          v-for="job in jobListings.slice(0, limit)"
          :key="job.id"
          :id="job.id"
          :title="job.title"
          :subtitle="job.subtitle"
          :description="job.description"
          :salary="job.salary"
          :location="job.location"
          :company="job.company"
          :type="job.type"
        />
      </div>
    </div>
  </section>
  <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
    <a
      href="/jobs"
      class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
      >View All Jobs</a
    >
  </section>
</template>
