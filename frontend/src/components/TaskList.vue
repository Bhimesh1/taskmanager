<template>
  <div>
    <h2>📋 Task List</h2>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        <div v-if="editingId === task.id">
          <input v-model="editTitle" placeholder="Title" />
          <input v-model="editDescription" placeholder="Description" />
          <select v-model="editStatus">
            <option value="pending">Pending</option>
            <option value="done">Done</option>
          </select>
          <button @click="saveEdit(task.id)">💾 Save</button>
          <button @click="cancelEdit">✖ Cancel</button>
        </div>
        <div v-else>
          <strong>{{ task.title }}</strong>: {{ task.description }} ({{ task.status }})
          <button @click="startEdit(task)">✏️ Edit</button>
          <button @click="deleteTask(task.id)">🗑 Delete</button>
        </div>
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
    const editingId = ref<number | null>(null)
    const editTitle = ref('')
    const editDescription = ref('')
    const editStatus = ref('pending')

    const fetchTasks = async () => {
      const response = await axios.get<Task[]>('http://localhost:8088/tasks')
      tasks.value = response.data
    }

    const deleteTask = async (id: number) => {
      await axios.delete(`http://localhost:8088/tasks/${id}`)
      await fetchTasks()
    }

    const startEdit = (task: Task) => {
      editingId.value = task.id
      editTitle.value = task.title
      editDescription.value = task.description
      editStatus.value = task.status
    }

    const cancelEdit = () => {
      editingId.value = null
    }

    const saveEdit = async (id: number) => {
      await axios.put(`http://localhost:8088/tasks/${id}`, {
        title: editTitle.value,
        description: editDescription.value,
        status: editStatus.value
      })
      editingId.value = null
      await fetchTasks()
    }

    onMounted(fetchTasks)

    return {
      tasks,
      editingId,
      editTitle,
      editDescription,
      editStatus,
      deleteTask,
      startEdit,
      cancelEdit,
      saveEdit
    }
  }
})
</script>
