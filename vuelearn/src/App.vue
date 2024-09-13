<script setup>
// composition api
// ref are like usestate in react
import { ref } from "vue";

const name = ref("Harish");
const status = ref("active");
const tasks = ref(["Task one", "Task Two", "Task three"]);
const link = "https://google.com";
const newTask = ref("");
const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};

const addTasks = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

const onMounted = async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log(error);
  }
};
onMounted();
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">Active user</p>
  <p v-else-if="status === 'pending'">Pending user</p>
  <p v-else>Pending user</p>

  <form @submit.prevent="addTasks">
    <label for="newTaks">New Tasks</label>
    <input type="text" v-model="newTask" name="newTasks" value="" newTaks />
    <button type="submit">submit</button>
  </form>

  <h1>Tasks</h1>
  <ul>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>
  <a v-bind:href="link">click me</a>
  <button @click.prevent="toggleStatus">Toggle</button>
</template>

<style scoped>
.task-manager {
  font-family: Arial, sans-serif;
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
}

h1,
h2 {
  color: #333;
}

.active {
  color: green;
}
.pending {
  color: orange;
}
.inactive {
  color: red;
}

.task-form {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input[type="text"] {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  padding: 8px 15px;
  background-color: #4caf50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

.task-list {
  list-style-type: none;
  padding: 0;
}

.task-list li {
  background-color: #f9f9f9;
  margin-bottom: 5px;
  padding: 10px;
  border-radius: 4px;
}

.link {
  display: inline-block;
  margin-top: 20px;
  color: #0066cc;
  text-decoration: none;
}

.toggle-btn {
  margin-top: 20px;
  background-color: #008cba;
}

.toggle-btn:hover {
  background-color: #007b9a;
}
</style>
