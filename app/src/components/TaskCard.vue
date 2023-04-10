<template>
  <div class="task-card my-style">
    <div>
      <h4>{{ model.title }}</h4>
      <p>{{ model.description }}</p>
    </div>
    <div>
      <my-button color="#61CE63" @click="emitOnDone" v-if="!model.status">DONE</my-button>
      <my-button @click="emitOnRemove" v-else>DELETE</my-button>
    </div>
  </div>

</template>

<script>
import MyButton from "@/components/MyButton.vue";

export default {
  components: {MyButton},
  emits: ['onDone', 'onRemove'],
  props: {
    model: {
      required: true,
      default: {
        id: 0,
        title: 'Create Video',
        description: 'And upload on YT',
        status: false
      }
    }
  },
  setup(props, {emit}) {
    const emitOnDone = () => {
      emit('OnDone')
    }

    const emitOnRemove = () => {
      emit('OnRemove')
    }

    return {
      emitOnRemove,
      emitOnDone
    }
  }
}
</script>

<style scoped>

input, button, .task-card {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.my-style {
  border-radius: 5px;
  border: solid 1px lightgray;
  padding: 5px;
  background-color: #f1f1f1;
  box-shadow: rgba(0, 0, 0, 0.12) 0px 1px 3px, rgba(0, 0, 0, 0.24) 0px 1px 2px;
}


</style>