<template>
  <div>
    <h1>TO DO</h1>
    <input
      type="text"
      class="add-input"
      autofocus="autofocus"
      placeholder="todo what?"
      @keydown.enter="addTodo"
    >
    <!--  v-bind:todo="todo" 父组件todo给子组件item传过去一个todo数据  -->
    <Item
      :todo="todo"
      v-for="todo in filteredTodos"
      :key="todo.id"
      @del="deleteTodo"
    ></Item>
    <Tabs
      :filter="filter"
      :todos="todos"
      @toggle="toggleFilter"
      @clearAll="clearAll"
    ></Tabs>
  </div>
</template>

<script>
import Item from '../../../components/item'
import Tabs from '../../../components/tabs'
let id = 0
export default {
  name: 'todo',
  components : {
    Item,
    Tabs
  },
  data () {
    return {
      todos: [],
      filter: 'all'
    }
  },
  computed: {
    filteredTodos() {
      if(this.filter === 'all') {
        return this.todos
      }
      const completed = this.filter === 'completed'
      return this.todos.filter(todo => completed === todo.completed)
    }
  },
  methods: {
    addTodo (e) {
      this.todos.unshift({
        id : id++,
        content: e.target.value.trim(),
        completed: false
      })
      e.target.value = ''
    },
    deleteTodo (id) {
      this.todos.splice(this.todos.findIndex(todo => todo.id === id), 1)
    },
    toggleFilter(state) {
      this.filter = state
    },
    clearAll() {
      this.todos = []
    }
  }
}
</script>

<style scoped>

</style>
