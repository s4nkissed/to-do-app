<template>
  <div class="task-input my-list">
    <input v-model="title" placeholder="Title" type="text">
    <input v-model="description" placeholder="Description" type="text">
    <my-button color="#c4c4c4" @click="onAddTask">ADD TASK</my-button>
  </div>
</template>

<script>
import {ref} from 'vue'
import MyButton from "@/components/MyButton.vue";

export default {
  components: {MyButton},
  emits: {
    onAddTask({title, description}) {
      if (title === '' || description === '') {
        alert('Input some info!')
        return false
      }
      return true
    }
  },
  setup(props, {emit}) {
    const title = ref('')
    const description = ref('')

    const onAddTask = () => {
      emit('onAddTask', {title: title.value, description: description.value})
      title.value = ''
      description.value = ''
    }

    return {
      title,
      description,
      onAddTask
    }
  }

}
</script>

<style lang="scss" scoped>
.my-list {
  display: grid;
  grid-template-rows: auto;
  grid-template-columns: 100%;
  grid-gap: 5px;
}

.task-input {
  margin: 10px 0;
}


</style>