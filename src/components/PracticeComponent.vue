<template>
  <div class="practice-component p-6 max-w-md mx-auto">
    <h2 class="text-2xl font-bold mb-4">Hello World</h2>

    <!-- Text entry html here -->
    <form method="POST" @submit.prevent="handleSubmit">
      <label class="mr-4">Task Name</label>
      <input v-model="form.taskName" type="text" class="border-2" /><br />
      <label class="mr-4">Task Due Date</label>
      <input v-model="form.dueDate" type="text" class="border-2" /><br />
      <label class="mr-4">Task Completion</label>
      <input v-model="form.complete" type="text" class="border-2" /><br />
      <button type="submit">Submit Text</button>
    </form>

    <div class="mt-10 bg-neutral-100 rounded-lg p-4">
      <h1 class="text-center font-bold text-xl">All Tasks</h1>
      <button class="bg-red-500 py-1 px-3 rounded-lg hover:bg-red-600 hover:cursor-pointer" @click="handleClearTasks">
        Clear All Tasks
      </button>
      <div v-for="(task, index) in tasks" :key="index" class="my-2 bg-neutral-200 rounded-lg p-2">
        Task Name: {{ task.taskName }} <br />
        Task Due Date: {{ task.dueDate }}<br />
        Task Complete: {{ task.complete }}
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

type Task = {
  taskName: string
  dueDate: string
  complete: string
}

const tasks = ref<Task[]>([{ taskName: 'abc', dueDate: '123', complete: 'true' }])

const form = ref({
  taskName: '',
  dueDate: '',
  complete: 'false',
})

defineOptions({
  name: 'PracticeComponent',
})
function handleSubmit() {
  tasks.value.push({
    taskName: form.value.taskName,
    dueDate: form.value.dueDate,
    complete: form.value.complete,
  })
}

function handleClearTasks() {
  tasks.value = []
}
</script>
<style lang="scss" scoped>
.practice-component {
  font-family: Arial, sans-serif;
}
</style>
