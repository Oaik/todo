<template>
  <div id="app" class="z-depth-5 blue-grey lighten-4">
    <h2>Todo List</h2>
    <input name="todo" type="text" placeholder="lets do a task" v-model="currentTodo">
    <button class="waves-effect waves-light btn" @click="addTodo" :disabled="isEmptyTodo">Add</button>
    <todo-item :todos="remainingTodo" :shown="true"/>
    <button class="btn" @click="showCompleted = !showCompleted">{{showCompleted ? "Hide" : "Show"}} Completed</button>
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
      ],
      currentTodo: "",
      currentId: 1,
      showCompleted: true
    }
  },
  methods: {
    addTodo: function() {
      this.todos.push({done: false, text: this.currentTodo, id: this.currentId})
      this.currentTodo = ""
      this.currentId = this.currentId + 1;
      console.log(this.currentId);
    },
    deleteTodo: function(currentTodo) {
      console.log(this.todos);
      this.todos = this.todos.filter(todo => todo.id != currentTodo.id)
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

<style lang="sass">
  body
    display: flex
    justify-content: center
    background-color: #90a4ae
  #app
    min-width: 50vw
    padding: 50px 25px
    min-height: 100vh
  h2
    text-align: center
  
  ul
    list-style: none
    padding: 0
  span
    color: #111
  [type="checkbox"]:checked+span
    text-decoration: line-through
    color: #9e9e9e
  ::placeholder
    color: #888 !important
</style>