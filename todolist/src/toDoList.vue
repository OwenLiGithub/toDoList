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
        <li v-for="(item,index) of showList" :key="index">
            <input type="checkbox" v-bind:checked="item.isChecked">
            <span>{{item.content}}</span>
        </li>
      </ol>
    <div>
      <ul id="filters">
                <li>
                    <a @click="all" >ALL</a>
                </li>
                <li>
                    <a @click="active" >Active</a>
                </li>
                <li>
                    <a @click="complete">Complete</a>
                </li>
            </ul>
    </div>
  </div>
</template>

<script >
export default {
 data(){
   return{
     msg:'',
     list:[],
     showList:[]
   }
 },
 methods:{
   handleclick(){
     let attribute = {
        content: this.msg,
        isChecked: false,
        isEdit: false
     }
     this.list.push(attribute)
     this.showList.push(attribute)
     this.msg = ''
   },
    complete(){
      this.showItems=this.list.filter((item)=>{
        return item.isChecked;
      })
    },
    active(){
      this.showItems=this.list.filter((item)=>{
        return !item.isChecked;
      })
    },
    all(){
      this.showItems=this.list
    }
 }
}
</script>
<style>
@import '../static/css/todolist.css';
</style>
