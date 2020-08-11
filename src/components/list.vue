<template>
  <ul>
    <li>{{data.title}}</li>
  </ul>
</template>
<script>
const data = [
  {
    title: 'Ant Design Title 1'
  },
  {
    title: 'Ant Design Title 2'
  },
  {
    title: 'Ant Design Title 3'
  },
  {
    title: 'Ant Design Title 4'
  }
]
export default {
  name: 'list',
  data () {
    return {
      data
    }
  }
}
</script>

<style scoped>

</style>
