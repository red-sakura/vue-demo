<template>
  <div>
    <a-row>
      <a-col :span="8">
      </a-col>
      <a-col :span="8">
        <a-card style="width: 400px">
          <h1>TO DO</h1>
          <div>
            <a-row>
              <a-col :span="16">
                <a-input placeholder="想要干什么?" style="width: 220px" v-model="data"/>              </a-col>
              <a-col :span="8">
                <a-button type="primary" @click="add">
                  添加
                </a-button>
             </a-col>
            </a-row>
          </div>
          <div>
            <List v-bind:title="input"></List>
          </div>
          <Button v-bind:title="input"></Button>
        </a-card>
      </a-col>
      <a-col :span="8">
      </a-col>
    </a-row>
  </div>
</template>

<script>
import List from '../../../components/list'
import Button from '../../../components/button'

export default {
  name: 'todo',
  components: {List,Button},
  data () {
    return {
      input: [],
      data: ''
    }
  },
  methods: {
    add: function () {
      if (this.data === ''){
        return
      }
      this.input.push(this.data)
      this.data = ''
    }
  }
}
</script>

<style scoped>

</style>
