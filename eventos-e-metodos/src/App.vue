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
      currentTask:'',
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
     
      this.tasks = this.tasks.map((item) => {
        if (item.id === task.id) {
          return { ...item, completed: !item.completed };
        }
        return {...item}
      });
    },
    addTask() {
      this.tasks.push({
        id: this.tasks.length,
        name: this.currentTask,
        completed: false
      });
      this.currentTask = ''
    }
  },
};
</script>

<template>
  <h1>Minha lista de Tarefas</h1>
  <button @click="showList = !showList">Ver a lista</button>
  <input type="text" v-focus v-model="currentTask" @keyup.enter="addTask()" />
  <ul v-if="showList">
    <li 
      v-for="task in tasks" 
      @dblclick="completeTask(task)" 
      :key="task.id"
      :class="{
        'line-throught': task.completed}">
      {{ task.name }}
      <button @click="remove(task.id)">&times;</button>
    </li>
  </ul>
</template>

<style scoped>
.line-throught {
  text-decoration: line-through;
}

</style>
