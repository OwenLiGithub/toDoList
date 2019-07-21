<template>
  <li>
      <input type="checkbox" ><span>{{content}}</span>
  </li>
</template>

<script>
export default {
  props:['content','index'],
  data () {
    return {
      msg: ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
