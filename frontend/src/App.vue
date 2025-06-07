<template>
  <div id="app">
    <h1>🗂️ Task Manager</h1>
    <TaskForm @task-added="refreshList" />
    <TaskList ref="listRef" />
  </div>
</template>

<script lang="ts">
import TaskForm from './components/TaskForm.vue'
import TaskList from './components/TaskList.vue'
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'App',
  components: {
    TaskForm,
    TaskList
  },
  setup() {
    const listRef = ref<InstanceType<typeof TaskList>>()

    const refreshList = () => {
      listRef.value?.$forceUpdate?.()
    }

    return {
      listRef,
      refreshList
    }
  }
})
</script>