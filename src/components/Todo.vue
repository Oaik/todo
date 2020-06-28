<template>
    <div>
    <ul v-if="shown">
      <li v-for="todo in todos" :key="todo.id">
        <label>
          <input type="checkbox" class="" :checked="todo.done" @click="toggleDone(todo)"> 
          <span>{{ todo.text }}</span>
        </label>
        <!-- <span @click="deleteTodo(todo)"> X</span> -->
      </li>
    </ul>
    </div>
</template>

<script>
export default {
  name: 'Item',
  props: ['todos', 'shown'],
  methods: {
    toggleDone: function(x) {
      x.done = !x.done;
    }
  },
}
</script>

<style lang="sass">
  [type="checkbox"]:checked+span
    text-decoration: line-through
</style>