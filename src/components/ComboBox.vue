<template>
  <select
    name="LeaveType"
    @change="sendTask(this.value)"
    class="form-control"
    v-model="title"
  >
    <option selected disabled hidden value="">Seleccione un elemento</option>
    <option v-for="task in tasks" v-bind:key="task.id">
      <Task v-bind:task="task" />
    </option>
  </select>
</template>

<script>
import Task from "./Task2";

export default {
  name: "ComboBox",
  props: ["tasks"],
  components: { Task },
  data() {
    return {
      title: "",
    };
  },
  methods: {
    sendTask() {
      this.$emit("notify-task", this.title);
    },
  },
};
</script>

<style scoped>
</style>