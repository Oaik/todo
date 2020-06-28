<template>
    <div>
    <ul v-if="shown">
      <li v-for="todo in todos" :key="todo">
        <input type="checkbox" :checked="todo.done" @click="toggleDone(todo)"> 
        {{ todo.text }}
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