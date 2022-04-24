<template>
  <div>
    <div class="card" :class="done ? 'done' : 'todo'">
      <span class="content" @click="$emit('handle')">
        <p v-if="done"><s >{{ content }}</s></p>
        <p v-else>{{ content }}</p>
      </span>
      <button @click="$emit('remove')">x</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
      required: true
    },

    content: {
      type: String,
      required: true
    },

    done: {
      type: Boolean,
      required: true
    }
  }
}
</script>

<style scoped>
  .card {
    display: flex;
    height: 100px;
    width: 200px;
    border: 1px solid black;

    /* padding: 1rem; */
  }
  .content {
    display: flex;
    flex-grow: 1;
    justify-content: center;
    align-items: center;
    height: 100%;

  }

  .todo {
    background-color: #d78b8b;
  }

  .done {
    background-color: #579f5c;
  }
</style>