<template>
  <div>
    <progress
      :value="progressValue"
      max="100"
      class="myProgress" />
  </div>
</template>

<script>
export default {
  props: {
    progressValue: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style scoped>
  .myProgress {
    width: 50vh;
    height: 2rem;
  }
</style>