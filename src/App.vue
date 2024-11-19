<script setup>
import { ref } from 'vue';

const name = ref("John Doe");
const status = ref("active");
const tasks = ref(["Task 1", "Task 2", "Task 3"]);

const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
}

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User online</p>
  <p v-else-if="status === 'inactive'">User offline</p>

  <h3>Tasks:</h3>
  <ol>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ol>
  <button @click="toggleStatus">Change user status</button>
</template>