<script>
export default {
  data() {
    return {
      name: "Tun tun mausi",
      status: "active",
      tasks: ["Task one", "Task Two", "Task three"],
      link: "https://google.com",
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
</template>
