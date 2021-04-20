<template>
  <div>
    {{ task.title }}
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ["task"],
  methods: {
    markComplete() {
      this.task.completed = !this.task.completed;
    },
  },
};
</script>

<style scoped>
</style>