<template>
  <div>
    <a-row>
      <a-col :span="8">
      </a-col>
      <a-col :span="8">
        <a-card style="width: 400px">
          <h1>TO DO</h1>
          <div>
            <a-input placeholder="想要干什么?" style="width: 200px"/>
            <a-button type="primary">
              添加
            </a-button>
          </div>
          <div>
            <List></List>
          </div>
        </a-card>
      </a-col>
      <a-col :span="8">
      </a-col>
    </a-row>
  </div>
</template>

<script>
import List from '../../../components/list'
export default {
  name: 'todo',
  components: {List}
}
</script>

<style scoped>

</style>
