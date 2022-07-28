
<template> 
     <div>
        <div v-bind:key="TodoTask.id" v-for=" TodoTask in TodoTask">
        <TodoItem v-bind:TodoTask="TodoTask" v-on:del="$emit('del', TodoTask.id)"/>
     
        </div>

    </div>
</template>

<script>

import TodoItem from './TodoItem';


export default{
    name: 'TodoTask',
    components:{
    TodoItem
},
    props: ["TodoTask"]
}


 </script>

<style scoped>

</style>> 





