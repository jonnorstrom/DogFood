<template>
  <ul>
    <li v-for="todo in someTodos" :key="todo.id" :class="{ success: todo.completed }">{{todo.title}}</li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      todos: []
    }
  },

  computed: {
    someTodos() {
      return this.todos.splice(0, 10)
    }
  },

  beforeMount() {
    fetch('https://jsonplaceholder.typicode.com/todos')
      .then(response => response.json())
      .then(json => this.todos = json)
  }
}
</script>

<style lang="css" scoped>
  .success {
    color: goldenrod;
  }

  li {
    text-align: left;
  }
</style>