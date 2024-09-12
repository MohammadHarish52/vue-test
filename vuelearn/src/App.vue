<script>
export default {
  data() {
    return {
      name: "Tun tun mausi",
      status: false,
    };
  },
};
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">Active user</p>
  <p v-else>user is inactive</p>
</template>
