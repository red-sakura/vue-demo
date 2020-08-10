<template>
  <div>
    <h1>hi</h1>
    <button v-on:click="clickfun">{{title}} You clicked me {{ count }} times.</button>
  </div>
</template>

<script>
export default {
  name: 'counter',
  props: ['title'],
  data () {
    return {
      count: 0
    }
  },
  methods: {
    clickfun: function () {
      this.count++
    }
  }
}
</script>

<style scoped>

</style>
