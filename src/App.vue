<template>
 <div class="container">
   <Header title="Task Tracker" @toggle-add-task="toggleAddTask" :showAddTask="showAddTask"/>
   <div v-show="showAddTask">
      <AddTasks @add-task="addTask"/>
   </div>
    
   <Tasks
   @togle-reminder="toggleReminder"
    @delete-task="deleteTask" :tasks='tasks'/>
  
 </div>
</template>

<script>
import Header from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTasks from './components/AddTasks.vue'

export default {
  name: 'App',
  components: {
   Header ,
   Tasks ,
   AddTasks 
  },
  data(){
    return{
      tasks:[],
      showAddTask:false
    }
  },
  created(){
    this.tasks=[
     {
       id:1,
       text:'React',
       day:'2021.07.01',
       reminder:'Joined'
     },
     {
       id:2,
       text:'React 2',
       day:'2021.07.01',
       reminder:true
     },
     {
       id:3,
       text:'Node ',
       day:'2021.07.02',
       reminder:true
     },
     {
       id:4,
       text:'Vue',
       day:'2021.07.03',
       reminder:true
     },
     {
       id:5,
       text:'Next',
       day:'2021.07.04',
       reminder:false
     }
    ]
  },
  methods:{
    toggleAddTask(){
      this.showAddTask=!this.showAddTask
    },
     deleteTask(id){
      if(confirm('Are You Sure')){
     this.tasks=this.tasks.filter((task)=>task.id!==id);
   }
    },

    toggleReminder(id){

      this.tasks=this.tasks.map((task)=>
      task.id === id ?  {...task,reminder:!task.reminder}:task)
    },

    addTask(newTask){
  this.tasks= [...this.tasks, newTask]
    }
  
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
