<template>
  <div>
    <div>
      <input type="text" placeholder="Add Something ..." v-model="todoText" @keyup.enter="addTodoList" />
      <button @click="addTodoList">&plus;</button>
    </div>
    <todo-list v-for="(todoItem, index) in dataTodoList" :todoItem="todoItem" :index="index" :key="index" ></todo-list>
  </div>
</template>
<script>
import TodoList from "./components/TodoList";
export default {
  components: {
    TodoList
  },
  data () {
    return {
      todoText: '',
      arrayTodoList: []
    }
  },
  computed: {
    dataTodoList () {
      return this.$store.getters.todos
    }
  },
  methods: {
    addTodoList() {
      this.arrayTodoList.push({
        todo: this.todoText,
        done: false
      });
      this.$store.commit('addTodoList', this.todoText)
      this.todoText = ''
      console.log(this.todoList);
    },
    remove(todos) {
      const index = this.todos.indexOf(todos);
      //   console.log(index)
      this.arrayTodoList.splice(index, 1);
      this.$store.commit('deleteTodo', index)
    }
  }
};
</script>