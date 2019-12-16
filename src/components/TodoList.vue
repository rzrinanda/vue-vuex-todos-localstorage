<template>
  <li>
    <h3>
      <input type="checkbox" @click="itemCheck(item)">
      <p>{{ index + 1 }} . {{ todoItem.text  }} </p>
      <p v-if="todoItem.done">finished</p>
      <button @click="deleteClick">Delete</button>
    </h3>
  </li>
</template>

<script>
export default {
  props: {
    todoItem: Object,
    index: Number
  },
  data () {
    return {
      checked: false
    }
  },
  methods: {
    itemCheck () {
      this.$store.commit('toggleTodo', this.index)
    },
    deleteClick () {
      this.$store.commit('deleteTodo', this.index)
    }
  }
}
</script>