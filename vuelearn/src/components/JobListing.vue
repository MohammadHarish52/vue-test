<script setup>
import { reactive, defineProps, onMounted } from "vue";
import JobListingCard from "./JobListingCard.vue";
import PulseLoader from "vue-spinner/src/PulseLoader.vue";
import axios from "axios";
defineProps({
  limit: {
    type: Number,
  },
  showButton: {
    type: Boolean,
    default: false,
  },
});

const state = reactive({
  jobListings: [],
  isLoading: true,
});

// Add this function to handle company data
onMounted(async () => {
  try {
    const response = await axios.get("/api/jobs");
    state.jobListings = response.data;
  } catch (error) {
    console.log("Error fetching jobs", error);
  } finally {
    state.isLoading = false;
  }
});
</script>

<template>
  <section class="bg-purple-50 px-4 py-10">
    <div class="container-xl lg:container m-auto">
      <h2 class="text-3xl font-bold text-purple-500 mb-6 text-center">
        Browse Jobs
      </h2>

      <div v-if="state.isLoading" class="text-3xl text-gray-500 py-6">
        <PulseLoader />
      </div>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <JobListingCard
          v-for="job in state.jobListings.slice(0, limit)"
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
