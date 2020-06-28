<template>
  <div id="app">
    <h2>Todo List</h2>
    <input type="text" v-model="currentTodo">
    <button @click="addTodo" :disabled="isEmptyTodo">Add</button>
    <todo-item :todos="remainingTodo" :shown="true"/>
    <button @click="showCompleted = !showCompleted">Show/hide completed</button>
    <todo-item :todos="completedTodo" :shown="showCompleted"></todo-item>
  </div>
</template>

<script>
import Todo from "./components/Todo.vue"
export default {
  name: 'App',
  components: {
    'todo-item': Todo
  },
  data: function() {
    return {
      todos: [
        {done: false, text: "buy milk"},
        {done: false, text: "solve a problem"},
        {done: true, text: "expert"}
      ],
      currentTodo: "",
      showCompleted: true
    }
  },
  methods: {
    addTodo: function() {
      this.todos.push({done: false, text: this.currentTodo})
    }
  },
  computed: {
    remainingTodo: function() {
      return this.todos.filter(x => !x.done);
    },
    completedTodo: function() {
      return this.todos.filter(x => x.done);
    },
    isEmptyTodo: function() {
      return this.currentTodo.trim() == '';
    }
  }
}
</script>

<style>
  ul {
    list-style: none;
    padding: 0;
  }
</style>