<script>
import { ref } from 'vue'
export default {
  data() {
    return {
      name: ref("John Doe"),
      status: ref('pending'),
      tasks: ref(['Task One', 'Task Two', 'Task Three']),
      link: 'https://google.com',
      newTask: ref('')
    }
  },

  methods: {
    toggleStatus() {
      if (this.status === 'active') {
        this.status = 'pending'
      } else if (this.status === 'pending') {
        this.status = 'inactive'
      } else {
        this.status = 'active'
      }
    }
  }
}
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else=>User is inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
  </form>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <p>{{ newTask }}</p>
  <a :href="link">Google</a>
  <br />
  <button v-on:click="toggleStatus">Toggle Status</button>
</template>

