<template>
  <div>
    <div v-bind:key="task.id" v-for="task in tasks">
      <Task v-bind:task="task" v-on:del-task="$emit('del-task', task.id)" />
    </div>
  </div>
</template>

<script>
import Task from "./Task";

export default {
  components: {
    Task,
  },
  name: "TaskManager",
  props: ["tasks"],
};
</script>

<style scoped>
</style>

<!--    

       
        se usa bind con el argumento key para setear
        una llave única para cada task
      -->