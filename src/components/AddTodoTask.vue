<template>
    <div>
        <form @submit="AddTodoTask">
            <input type="text" v-model="title" name="title" placeholder="Add Todotask...">
            <input type="submit" class="btn" value="Submit ">
        </form>
 </div>
</template>

<script>
export default {

    name: "AddTodoTask",
    data(){
        return{
            title:""
        }
    },
    methods: {
        AddTodoTask(e){
            e.preventDefault();
            const newTodoTask ={
                id: 4,
                title: this.title,
                completed: false
            }
            //send via emmit
            this.$emit('Add-TodoTask', newTodoTask);
            this.title="";
        }
    }
    }
</script>


<style scoped>
    form{
        display: flex;
    }
    input[type="text"]{
        flex:10;
        padding: 5px;
    }
    input[type="button"] {
    flex:2
    }

    


</style>