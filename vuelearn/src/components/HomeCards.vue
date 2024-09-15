<script setup>
import Card from "./Card.vue";
</script>

<template>
  <section class="py-4">
    <div class="container-xl lg:container m-auto">
      <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
        <Card
          title="For Developers"
          description="Browse our jobs and start your career today"
          btnText="Browse Jobs"
        />
        <Card
          background="bg-purple-100"
          title="For Employers"
          description="List your job to find the perfect developer for the role"
          btnColor="bg-purple-500"
        />
      </div>
    </div>
  </section>
</template>
