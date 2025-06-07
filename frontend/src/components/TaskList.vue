<template>
  <div>
    <h2>📋 Task List</h2>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <strong>{{ task.title }}</strong>: {{ task.description }} ({{ task.status }})
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import axios from 'axios'
import { defineComponent, onMounted, ref } from 'vue'
import type { Task } from '../../types'


export default defineComponent({
  name: 'TaskList',
  setup() {
    const tasks = ref<Task[]>([])

    const fetchTasks = async () => {
      const response = await axios.get<Task[]>('http://localhost:8088/tasks')
      tasks.value = response.data
    }

    onMounted(fetchTasks)

    return {
      tasks
    }
  }
})
</script>
