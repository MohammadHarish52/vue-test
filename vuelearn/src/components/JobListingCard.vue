<script setup>
import { defineProps, ref, computed } from "vue";
import { RouterLink } from "vue-router";

const props = defineProps({
  id: {
    type: Number, // Accept both String and Number
    required: true,
  },
  title: String,
  description: String,
  salary: String,
  location: String,
  company: {
    type: [String, Object], // Accept both String and Object
    required: true,
  },
  type: {
    type: String,
    default: "Full-Time",
  },
});

const showFullDescription = ref(false);

const toggleDescription = () => {
  showFullDescription.value = !showFullDescription.value;
};

const truncatedDescription = computed(() => {
  let description = props.description;
  if (!showFullDescription.value) {
    description = description.substring(0, 90) + "...";
  }
  return description;
});
</script>

<template>
  <div class="bg-white rounded-xl shadow-md relative">
    <div class="p-4">
      <div class="mb-6">
        <div class="text-gray-600 my-2">{{ type }}</div>
        <h3 class="text-xl font-bold">{{ title }}</h3>
      </div>

      <div class="mb-5">
        {{ truncatedDescription }}
        <!-- Use truncatedDescription -->

        <button
          @click.prevent="toggleDescription"
          className="text-purple-500 hover:text-purple-600"
        >
          {{ showFullDescription ? "less" : "more" }}
        </button>
      </div>

      <h3 class="text-purple-500 mb-2">{{ salary }} / Year</h3>

      <div class="border border-gray-100 mb-5"></div>

      <div class="flex flex-col lg:flex-row justify-between mb-4">
        <div class="text-orange-700 mb-3">
          <i class="pi pi-map-marker"></i>
          {{ location }}
        </div>
        <div class="text-blue-600 mb-3">
          {{ typeof company === "object" ? company.name : company }}
        </div>
        <RouterLink
          :to="{ name: 'job', params: { id: id } }"
          class="h-[36px] bg-purple-500 hover:bg-purple-600 text-white px-4 py-2 rounded-lg text-center text-sm"
        >
          Read More
        </RouterLink>
      </div>
    </div>
  </div>
</template>
