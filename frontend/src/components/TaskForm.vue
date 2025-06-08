<template>
  <div>
    <h2>➕ Add Task</h2>
    <form @submit.prevent="submitTask">
      <input v-model="title" placeholder="Title" required />
      <input v-model="description" placeholder="Description" required />
      <select v-model="status">
        <option value="pending">Pending</option>
        <option value="done">Done</option>
      </select>
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<script lang="ts">
import axios from 'axios'
import { defineComponent, ref } from 'vue'
import type { Task } from '@/types'


export default defineComponent({
  name: 'TaskForm',
  emits: ['task-added'],
  setup(_, { emit }) {
    const title = ref('')
    const description = ref('')
    const status = ref('pending')

    const submitTask = async () => {
      await axios.post('http://localhost:8088/tasks', {
        title: title.value,
        description: description.value,
        status: status.value
      })
      title.value = ''
      description.value = ''
      status.value = 'pending'
      emit('task-added')
    }

    return {
      title,
      description,
      status,
      submitTask
    }
  }
})
</script>
