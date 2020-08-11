<template>
  <div>
    <ol>
      <li v-for="todo,index in title">
        <a-row>
          <a-col :span="8">
            <a-checkbox @change="onChange"></a-checkbox>
          </a-col>
          <a-col :span="8">
            <span v-bind:class="through">{{title[index]}}</span>
          </a-col>
          <a-col :span="8">
            <a-button @click="deleteArray(index)" type="danger">删除</a-button>          </a-col>
        </a-row>
      </li>
    </ol>
  </div>
</template>
<script>

export default {
  name: 'list',
  props: ['title'],
  data () {
    return {
      through: 'off'
    }
  },
  methods: {
    deleteArray: function (index) {
      this.title.splice(index, 1)
    },
    onChange (e) {
      if (e.target.checked) {
        this.through = 'on'
      } else {
        this.through = 'off'
      }
    }
  }
}
</script>

<style scoped>
button{
  cursor: pointer;
}
ol{
  list-style-type:none;
  text-align: left;

}
.on{
  text-decoration:line-through;
}
</style>
