<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <EntryForm :clickHandler="addFood"/>
    <DogFoodList :foodList="foodList" :clickHandler="removeFood"/>
    <ul>
      <li v-for="todo in someTodos" :key="todo.id" :class="{ success: todo.completed }">{{todo.title}}</li>
    </ul>
  </div>
</template>

<script>
import EntryForm from './components/EntryForm.vue'
import DogFoodList from './components/DogFoodList.vue'

export default {
  name: 'app',
  components: {
    EntryForm,
    DogFoodList
  },

  data() {
    return {
      foodList: [],
      todos: []
    }
  },

  computed: {
    someTodos() {
      return this.todos.splice(0, 10)
    }
  },

  methods: {
    addFood(food) {
      this.foodList.push(food)
    },

    removeFood(i) {
      this.foodList.splice(i, 1)
    }
  },

  created() {
    fetch('https://jsonplaceholder.typicode.com/todos')
      .then(response => response.json())
      .then(json => this.todos = json)
  }
}
</script>

<style scoped>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.success {
  color: goldenrod;
}

li {
  text-align: left;
}
</style>
