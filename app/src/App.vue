<template>
  <main>
    <h1 class="header">TODO LIST</h1>
    <task-input @onAddTask="addTask"></task-input>
    <ul class="task-list my-list">
      <li v-for="item in taskList" :key="item.id">
        <task-card @onRemove="removeTask(item.id)" @onDone="setDoneTask(item.id)" :model="item"></task-card>
      </li>
    </ul>
  </main>
</template>

<script setup>
import TaskCard from "@/components/TaskCard.vue";
import TaskInput from "@/components/TaskInput.vue";
import {ref} from 'vue';

const taskList = ref([{id: 0, title: 'Create video', description: 'And upload on YT', status: false}])

const addTask = ({title, description}) => {
  if (title && description) {
    taskList.value.push({
      id: taskList.value.length,
      title,
      description,
      status: false
    })
  }

}
const setDoneTask = (id) => {
  taskList.value = taskList.value.map(x => {
    if (x.id === id)
      x.status = true
    return x
  })
}
const removeTask = (id) => {
  taskList.value = taskList.value.filter(x => x.id !== id)
}
</script>

<style>
* {
  font-family: "JetBrains Mono", monospace;
  margin: 0;
  padding: 0;
}

main {
  max-width: 600px;
  margin: auto;
}

.task-list {
  list-style: none;
}

.header {
  display: flex;
  justify-content: center;
  align-items: center;
}

</style>