<template>


  <div class="bg-gray-600 text-white w-1/2 m-auto mt-12">

    <div class="text-center border-b-2 border-black py-4">
      <h1 class="text-3xl py-4">Todo Zeugs</h1>
      <p class="text-xl" v-if="openTodos.length>0">Hier bitte machen :) noch offen({{ openTodos.length }})</p>
      <p class="text-xl" v-else>gz Bruder, alles done</p>
      <div class="mt-4">
        <input type="text" class="py-2 w2/3 text-black" v-model="newTodo"/>
        <button class="bg-red-400 py-2 w1/3" @click="addTodo">Add</button>
      </div>
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
      newTodo: "",
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
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    addTodo() {
      this.todos.push({todo: this.newTodo, done: false})
    },
  },
  computed: {
    openTodos() {
      const openTodos = this.todos.filter((todo) => {
        return !todo.done
      });
      return openTodos;
    },
  },
}
</script>

