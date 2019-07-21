<template>
  <div id="app" class="container">
    <div>
      <h2>Jquery To Do List</h2>
       <p>
            <em>Simple Todo List with adding and filter by diff status.</em>
         </p>
    </div>
    <div>
            <input class="input-text" type="text" name="ListItem"  v-model="msg">
            <div id="button" @click="handleclick">Add</div>
    </div>
   <br>
      <ol>
        <todo-item v-for="(item,index) of list" :key="index"
        :content="item" :indexItem="index"
        @delete="handledelete"
        @checked="handledchecked"
        ></todo-item>
      </ol>
    <div>
      <ul id="filters">
                <li>
                    <a href="#" >ALL</a>
                </li>
                <li>
                    <a href="#" >Active</a>
                </li>
                <li>
                    <a href="#">Complete</a>
                </li>
            </ul>
    </div>
  </div>
</template>

<script >
import todoitem from './components/todoitem'
export default {
 components:{
   'todo-item':todoitem
 },
 data(){
   return{
     msg:'',
     list:[],
     checkedList:[]
   }
 },
 methods:{
   handleclick(){
     this.list.push(this.msg),
     this.msg = ''
   },
   handledelete(index){
     this.list.splice(index-1,1)
   },
    handledchecked(index){
     this.checkedList.push(this.list[index])
   }
 }
}
</script>
<style>
@import '../static/css/todolist.css';
</style>
