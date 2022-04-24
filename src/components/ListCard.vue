<template>
  <div>
    <div class="listTasks">
      <TaskCard
        v-for="(todo, index) in todos"
        :id="index"
        :content="todo.content"
        :done="todo.done"
        :key="index"
        @remove="$emit('remove', index)"
        @handle="$emit('handle', index)" />
    </div>
  </div>
</template>

<script>
import TaskCard from './TaskCard.vue'

export default {
  components: {
    TaskCard
  },

  props: {
    todos: {
      type: Array
    }
  }
}
</script>

<style scoped>
.listTasks {
  margin-top: 2rem;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: flex-start;
  gap: 1rem;
}
</style>