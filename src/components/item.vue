<template>
 <div :class="['todo-item',todo.completed ? 'completed' : '']">
   <input
     type="checkbox"
     class="toggle"
     v-model="todo.completed"
   >
   <label>{{todo.content}}</label>
   <button
   @click="deleteTodo"
   >delete</button>
 </div>
</template>

<script>
export default {
  name: 'item',
  props: {
    todo : {
      type : Object,
      required: true
    }
  },
  methods : {
    deleteTodo () {
    //  触发父组件的方法
      this.$emit('del', this.todo.id)
    }
  }
}
</script>

<style scoped>

</style>
