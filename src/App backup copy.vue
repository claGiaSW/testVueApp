<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const name = ref("John Doe");
const status = ref("active");
const tasks = ref(["Task 1", "Task 2", "Task 3"]);
const newTask = ref("");

const toggleStatus = () => {
  status.value = status.value === "active" ? "inactive" : "active";
}

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
}

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
}

onMounted(async () => {
  try {
    const response = await axios.get("https://jsonplaceholder.typicode.com/todos");
    tasks.value = response.data.map((task) => task.title);
  } catch (error) {
    console.error(`Error fetching tasks: ${error}`);
  }

})

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User online</p>
  <p v-else-if="status === 'inactive'">User offline</p>
  <button @click="toggleStatus">Change user status</button>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">submit</button>
  </form>

  <h3>Tasks:</h3>
  <ol>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ol>
</template>