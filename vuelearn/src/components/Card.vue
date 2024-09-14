<script setup>
import { defineProps } from "vue";

defineProps({
  background: {
    type: String,
    default: "bg-gray-100",
  },
  title: {
    type: String,
    default: "Test title",
  },
  description: {
    type: String,
    default: "Test description",
  },
  btnText: {
    type: String,
    default: "Test button text",
  },
  btnColor: {
    type: String,
    default: "bg-black",
  },
});
</script>

<template>
  <div :class="[background, 'p-6', 'rounded-lg', 'shadow-md']">
    <h2 class="text-2xl font-bold">{{ title }}</h2>
    <p class="mt-2 mb-4">{{ description }}</p>
    <a
      href="jobs.html"
      :class="[
        btnColor,
        'text-white',
        'rounded-lg',
        'px-4',
        'py-2',
        'hover:bg-gray-700',
      ]"
    >
      {{ btnText }}
    </a>
  </div>
</template>
