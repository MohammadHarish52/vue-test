<script>
export default {
  data() {
    return {
      name: "Tun tun mausi",
      status: "active",
    };
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">Active user</p>
  <p v-else-if="status === 'pending'">Pending user</p>
  <p v-else>Pending user</p>
</template>
