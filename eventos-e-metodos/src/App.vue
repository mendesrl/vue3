<script>
const focus = {
  inserted: (el) => {
    el.focus();
  },
};

export default {
  directives: { focus },
  data() {
    return {
      showList: false,
      tasks: [
        { id: 1, name: "Estudar vue", completed: false },
        { id: 2, name: "Estudar react", completed: false },
      ],
    };
  },
  methods: {
    remove(id) {
      this.tasks = this.tasks.filter((item) => item.id != id);
    },
    completeTask(task) {
      console.log("teste", task);
      this.tasks = this.tasks.map((item) => {
        if (item.id === task.id) {
          return { ...item, completed: !item.completed };
        }
      });
    },
  },
};
</script>

<template>
  <h1>Minha lista de Tarefas</h1>
  <button @click="showList = !showList">Ver a lista</button>
  <input type="text" v-focus />
  <ul v-if="showList">
    <li v-for="task in tasks" @dblclick="completeTask(task)" :key="task.id">
      {{ task.name }}
      <button @click="remove(task.id)">&times;</button>
    </li>
  </ul>
</template>

<style scoped></style>
