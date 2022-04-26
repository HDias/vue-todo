<template>
  <div>
    <div>
      <input
        type="text"
        v-model="value"
        @keyup.enter="addCard"
        maxlength="100"
        placeholder="Nova Tarefa"
      />
      <button @click="addCard">+</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: null,
    };
  },

  methods: {
    addCard() {
      if (this.value) {
        this.$emit("task", { content: this.value, done: false });
        this.value = null;

        return;
      }

      throw "Digite algum valor para criar um TODO";
    },
  },
};
</script>

<style>
</style>