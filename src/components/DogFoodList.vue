<template>
  <div>
    <p v-for="(food, i) in foodList" :key="food">{{ food | capitalize }} | 
      <a @click.prevent="clickHandler(i)">Remove</a>
    </p>
  </div>
</template>

<script>
export default {
  props: {
    foodList: {
      type: Array,
      default: () => ["Puppy Chow", "Blue Buffalo"]
    },
    clickHandler: Function
  },
  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }
}
</script>

<style scoped>
  a {
    text-decoration: underline;
  }
</style>


