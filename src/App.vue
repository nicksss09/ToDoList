<template>
  <div id="app">
    <HeaderKo/>
    <AddTodoTask v-on:Add-TodoTask="AddTodoTask" />
    <TodoTask v-bind:TodoTask="TodoTask" v-on:del="todo" />
  </div>
 
 
</template>


<script>

import TodoTask from './components/TodoTask';
import AddTodoTask from './components/AddTodoTask';
import HeaderKo from './components/layout/HeaderKo';
import axios from 'axios'; 

export default {
  name: 'app',
  components: {
    TodoTask,
    HeaderKo,
    AddTodoTask
    
    
},
  data(){
    return{
      TodoTask:[]
    }
  },
  methods:{
    todo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => {
        this.TodoTask = this.TodoTask.filter(TodoTask => TodoTask.id !== id);
        return res
      })
      .catch(error => {
      return Promise.reject(error);
    })
    },



    AddTodoTask(newTodoTask){
      const {title, completed } = newTodoTask;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res =>this.TodoTask =[...this.TodoTask,res.data])
      .catch(error => {
      return Promise.reject(error);
    })
    }
    
  },


  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5 ')
    .then(res => this.TodoTask = res.data)
    .catch(error => {
      return Promise.reject(error);

    })
  }

} 

</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;




}
.btn{
  color:white;
  background-color:blue;
}

body{
  font-family: Arial, Helvetica, sans-serif;
}
.btn{
  display: inline;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover{
  background: #666;
}
</style>
