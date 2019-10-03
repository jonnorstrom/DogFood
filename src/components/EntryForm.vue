<template>
  <div>
    <form v-on:submit.prevent="submitFood">
      <input type="text" v-model="foodName" placeholder="Dogfood Name">
      <button type="submit">Add Food</button>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    clickHandler: Function
  },
  data() {
    return {
      foodName: ""
    }
  },
  methods: {
    submitFood() {
      this.clickHandler(this.foodName)
      this.foodName = ""
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
