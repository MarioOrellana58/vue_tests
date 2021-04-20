<template>
  <div id="app">
    <Header />
    <AddTask v-on:add-task="addTask" />
    <TaskManager v-bind:tasks="tasks" v-on:del-task="deleteTask" />
    <ComboBox v-bind:tasks="tasks" v-on:notify-task="notifyTask" />
    <p>{{ msm }}</p>
  </div>
</template>

<script>
import TaskManager from "./components/TaskManager";
import AddTask from "./components/AddTask";
import Header from "./components/layout/Header";
import ComboBox from "./components/ComboBox";
import "v-slim-dialog/dist/v-slim-dialog.css";
import SlimDialog from "v-slim-dialog";
import Vue from "vue";

export default {
  name: "App",
  components: {
    TaskManager,
    Header,
    AddTask,
    ComboBox,
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: "Task 1",
          completed: false,
        },
        {
          id: 2,
          title: "Task 2",
          completed: false,
        },
        {
          id: 3,
          title: "Task 3",
          completed: false,
        },
      ],
      msm: "",
    };
  },
  methods: {
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },

    addTask(task) {
      if (task.title !== "") {
        this.tasks.push(task);
      } else {
        Vue.use(SlimDialog);
      }
    },
    showAlert() {
      const options = { title: "Error", size: "sm" };
      this.$dialogs
        .alert("No se pueden añadir tareas vacías", options)
        .then((res) => {
          console.log(res); // {ok: true|false|undefined}
        });
    },
    notifyTask(val) {
      this.msm = "Usted seleccionó: " + val;
    },
  },
};
</script>

<style>
</style>
