<template>
<div>
    <div v-for="task in tasks" :key="task.id" >
        <Task 
        @togle-reminder="$emit('togle-reminder',task.id)"
        @delete-task="$emit('delete-task',task.id)"
         :task="task"/>
    </div>
</div>
    
</template>

<script>
import Task from './Task.vue'
export default {
    
   name:'Tasks',
   emits:['deleteTask','togle-reminder'],
   props:{
       tasks:Array
   },
   components:{
       Task
   }
    
}
</script>

<style >

</style>