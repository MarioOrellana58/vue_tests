<template>
  <div>
    <form @submit="addTask">
      <input type="text" v-model="title" name="title" placeholder="Add Task" />
      <input type="submit" value="Add Task" />
    </form>
  </div>
</template>

<script>
var a = 3;
export default {
  name: "AddTask",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addTask(e) {
      e.preventDefault();
      a++;
      const task = {
        id: a,
        title: this.title,
        completed: false,
      };
      this.$emit("add-task", task);
    },
  },
};
</script>

<style scoped>
</style>