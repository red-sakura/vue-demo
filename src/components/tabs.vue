<template>
 <div>
   <span>{{unFinishedTodoLength}} 完成</span>
   <span>
     <!--     -->
     <span
     v-for="state in states"
     :key="state"
     :class="[state,filter === state ? 'actived' : '']"
     @click="toggleFilter(state)"
     >
       <button>{{state}}</button>
     </span>
   </span>
   <span class="clear" @click="clearAllCompleted"><button>全部删除</button></span>
 </div>
</template>

<script>
export default {
  name: 'tabs',
  // 接收父组件传来的值
  props:{
    filter: {
      type: String,
      required: true
    },
    todos: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      states: ['all','active','completed']
    }
  },
  computed: {
   unFinishedTodoLength() {
     return this.todos.filter(todo => !todo.completed).length
   }
  },
  methods : {
    clearAllCompleted () {
      this.$emit('clearAll')
    },
    toggleFilter (state) {
      this.$emit('toggle',state)

    }
  }
}
</script>

<style scoped>
 .actived{
   color: red;
 }
</style>
