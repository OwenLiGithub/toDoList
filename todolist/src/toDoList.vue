<template>
  <div id="app">
    <input v-model="msg"><button @click="handleclick">change</button>
    <div>
      <ul>
        <todo-item v-for="(item,index) of list" :key="index"
        :content="item" :indexItem="index"
        @delete="handledelete"
        ></todo-item>
      </ul>
    </div>
  </div>
</template>

<script>
import todoitem from './components/todoitem'
export default {
 components:{
   'todo-item':todoitem
 },
 data(){
   return{
     msg:'',
     list:[]
   }
 },
 methods:{
   handleclick(){
     this.list.push(this.msg),
     this.msg = ''
   },
   handledelete(index){
     this.list.splice(index-1,1)
   }
 }
}
</script>

<style>
</style>
