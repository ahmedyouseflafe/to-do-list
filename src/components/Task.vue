<template>
  <div class="container">
    <div class="task">
      <!-- title -->
      <div class="title">
        <h1>To Do List</h1>
      </div>
 
 
 
    
      <!-- form -->
      <div class="form">
        <input
          type="text"
          placeholder="New Task"
          v-model="newTask"
          @keyup.enter="addTask"
        />
        <button @click="addTask"><i class="fas fa-plus"></i></button>
        
      </div>
      <!-- task lists -->
      <div class="taskItems">
        <ul>
          <task-item
            v-bind:task="task"
            v-for="(task,index) in tasks"
            :key="task.id"
            @remove="removeTask(index)"
            @complete="completeTask(task)"
            
            
          ></task-item>
        </ul>
      </div>
      <!-- buttons -->
      <div class="clearBtns">
        <!-- <button @click="clearCompleted">Clear completed</button> -->
        <button @click="clearAll">Clear all</button>
      </div>
      <!-- pending task -->
      <div class="pendingTasks">
        <span>Completed Tasks: {{ inCompleted }}</span>
        
      
      </div>
    </div>
  </div>
</template>

<script>

import taskItem from "./task-item.vue";
import moment from 'moment';



export default {
  name: "Task",
  props: ["tasks"],
  components: {
    taskItem,
    
  },
  data() {
    return {
      newtask: "",
    };
  },
  
  computed: {
    inCompleted() {
      return this.tasks.filter(this.inprogress).length;
    },
    
  },
  methods: {
    addTask() {
      if (this.newTask) {
        this.tasks.push({
          title: this.newTask,
          completed: false,
          date:moment(this.date).format('YYYY-MM-DD')
        });
        this.newTask = "";
      }
    },

    inprogress(task) {
      return !this.isCompleted(task);
    },
    isCompleted(task) {
      return !task.completed;
    },
    clearCompleted() {
      this.tasks = this.tasks.filter(this.inprogress);
    },
    clearAll() {
      this.tasks = [];
    },
    removeTask(index){
      this.tasks.splice(index,1)
    },
    completeTask(task){

      task.completed = !task.completed;

    },
    persentag(){

return this.persentag = this.completeTask/this.task

    },
   
     
  },
};
</script>
