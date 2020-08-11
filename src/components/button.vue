<template>
  <a-row>
    <a-col :span="6">
      <a-button class="button">全部</a-button>
    </a-col>
    <a-col :span="6">
      <a-button class="button">未执行</a-button>
    </a-col>
    <a-col :span="6">
      <a-button class="button">已执行</a-button>
    </a-col>
    <a-col :span="6">
      <a-button class="button" @click="clear" type="danger">清空</a-button>
    </a-col>
  </a-row>
</template>

<script>
export default {
  name: 'button',
  props: ['title'],
  data () {
    return {
      all: [],
      done: [],
      undone: []
    }
  },
  methods: {
    clear: function () {
      this.title.splice(0)
    }
  },
  created: function () {
    this.all = this.title
  }
}
</script>

<style scoped>
.button{
  width: 70px;
}
</style>
