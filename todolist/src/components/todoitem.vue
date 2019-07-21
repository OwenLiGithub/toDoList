<template>
 <li @click="deleteitem">{{content}}</li>
</template>

<script>
export default {
  props:['content','index'],
  methods:{
      deleteitem(){
          this.$emit('delete',this.index)
      }
  }

}
</script>

<style scoped>

</style>
