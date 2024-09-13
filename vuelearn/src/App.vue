<script>
// composition api
import { ref } from "vue";
export default {
  setup() {
    const name = ref("Harish");
    const status = ref("active");
    const tasks = ["Task one", "Task Two", "Task three"];
    const link = "https://google.com";
    const toggleStatus = () => {
      if (status.value === "active") {
        status.value = "pending";
      } else if (status.value === "pending") {
        status.value = "inactive";
      } else {
        status.value = "active";
      }
    };
    return {
      name,
      status,
      tasks,
      link,
      toggleStatus,
    };
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">Active user</p>
  <p v-else-if="status === 'pending'">Pending user</p>
  <p v-else>Pending user</p>

  <h1>Tasks</h1>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a v-bind:href="link">click me</a>
  <button @click="toggleStatus">Toggle</button>
</template>
