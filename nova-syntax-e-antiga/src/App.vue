<template>
  <h1>Minha lista de Tarefas</h1>
  <button @click="state.showList = !state.showList">Ver a lista</button>
  <input
    type="text"
    v-focus
    v-model="state.currentTask"
    @keyup.enter="addTask()"
  />
  <ul v-if="state.showList">
    <li
      v-for="task in state.tasks"
      @dblclick="completeTask(task)"
      :key="task.id"
      :class="{
        'line-throught': task.completed,
      }"
    >
      {{ task.name }}
      <button @click="remove(task.id)">&times;</button>
    </li>
  </ul>
</template>

<script>
  import { reactive } from "vue";

  const focus = {
    inserted: (el) => {
      el.focus();
    },
  };

  export default {
    name: "App",
    components: {},
    directives: { focus },
    setup() {
      const state = reactive({
        showList: false,
        currentTask: "",
        tasks: [
          { id: 1, name: "Estudar vue", completed: false },
          { id: 2, name: "Estudar react", completed: false },
        ],
      });

      function remove(id) {
        state.tasks = state.tasks.filter((item) => item.id != id);
      }
      function completeTask(task) {
        state.tasks = state.tasks.map((item) => {
          if (item.id === task.id) {
            return { ...item, completed: !item.completed };
          }
          return { ...item };
        });
      }
      function addTask() {
        state.tasks.push({
          id: state.tasks.length,
          name: state.currentTask,
          completed: false,
        });
        state.currentTask = "";
      }
      return {
        state,
        remove,
        addTask,
        completeTask
      }
    },
  };
</script>

<style></style>
