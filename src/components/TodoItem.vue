<template>
    <div class="TodoTask-item" v-bind:class="{'is-completed':TodoTask.completed}">
    <p>
        <input type="checkbox" v-on:change="markComplete" v-bind:checked="TodoTask.completed">
        {{TodoTask.title}}
        <button v-on:click="$emit('del', TodoTask.id)" class="del">DELETE</button>
        </p>
        </div>
</template>
<script>
export default{
    name: "TodoItem",
    props:["TodoTask"],

    data(){
        return{
            task:this.TodoTask,
        }
    },
    methods:{
    markComplete(){
        this.task.completed = !this.task.completed;
    }
}
}

    


</script>

<style  scoped>
.TodoTask-item{
    background-color: pink;
    padding: 10px;
    border-bottom: 1px #ccc dotted;  
}

    .is-completed{
        text-decoration: line-through;
    
    }

    .del{
        background-color: white;
        color: black;
        border: none;
        padding: 5x 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }



</style>
