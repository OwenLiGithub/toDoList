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
            <input type="checkbox" v-model="item.isChecked">
            <input type="text" v-if="item.isEdit" v-model="item.content" @keyup.enter="onSubmit(index)">
              <span v-else @dblclick="onDblclick(index)">
                  <del v-if="item.isChecked">{{item.content}}</del>
                  <span v-else>{{item.content}}</span>
              </span>
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
      this.showList = this.list.filter((item)=>{
        return item.isChecked;
      })
    },
    active(){
      this.showList=this.list.filter((item)=>{
        return !item.isChecked;
      })
    },
    all(){
      this.showList = this.list
    },
    onDblclick(index){
      this.showList[index].isEdit = true
    },
    onSubmit(index){
        this.showList[index].isEdit=false
    }
 }
}
</script>
<style>
@import '../static/css/todolist.css';
</style>
