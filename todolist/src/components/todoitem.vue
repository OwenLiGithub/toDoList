<template>
  <li>
      <Checkbox v-model="licontent.isChecked">
    </Checkbox><span>{{licontent.msg}}</span>
  </li>
</template>

<script>
export default {
  props:['licontent','index'],
  data () {
    return {
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
