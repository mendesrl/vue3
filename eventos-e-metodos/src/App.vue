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
};
</script>

<template>
  <h1>Minha lista de Tarefas</h1>
  <button @click="showList = !showList">Ver a lista</button>
  <input type="text" v-focus />
  <ul v-if="showList">
    <li v-for="task in tasks" :key="task.id">{{ task.name }}</li>
  </ul>
</template>

<style scoped>
</style>
