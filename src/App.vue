<template>


  <div class="bg-gray-600 text-white w-1/2 m-auto mt-12">

    <div class="text-center border-b-2 border-black py-4">
      <h1 class="text-3xl py-4">Todo Zeugs</h1>
      <p class="text-xl">Hier bitte machen :) noch offen({{ todos.length }})</p>
    </div>
    <div v-for="(todo, index) in todos" :key="todo.todo">
      <Todo :todoprop="todo" :todoindex="index" @toggledone-index="toggleDone" @deletetodo-index="deleteTodo"/>
    </div>


  </div>
</template>

<script>
import Todo from './components/Todo.vue';


export default {
  name: 'App',
  data() {
    return {
      todos: [
        {todo: "Einkaufen", done: false},
        {todo: "Auskaufen", done: false},
        {todo: "Fabians Reifen einbunkern", done: true},
      ]
    }
  },
  components: {
    Todo
  },
  methods: {
    toggleDone(index) {
      this.todos[index].done = !this.todos[index].done;
    },
    deleteTodo(index){
      this.todos.splice(index, 1);
    },
  }
}
</script>

