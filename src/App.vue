<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <EntryForm :clickHandler="addFood"/>
    <DogFoodList :foodList="foodList" :clickHandler="removeFood"/>
    <Todos></Todos>
  </div>
</template>

<script>
import EntryForm from './components/EntryForm.vue'
import DogFoodList from './components/DogFoodList.vue'
import Todos from './components/Todos.vue'
export default {
  name: 'app',
  components: {
    EntryForm,
    DogFoodList,
    Todos
},

  data() {
    return {
      foodList: []
    }
  },

  methods: {
    addFood(food) {
      this.foodList.push(food)
    },

    removeFood(i) {
      this.foodList.splice(i, 1)
    }
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
</style>
