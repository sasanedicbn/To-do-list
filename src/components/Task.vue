<template>
    <div class="container">
      <div class="task">
        <!-- title -->
        <div class="title">
          <h1>To Do List</h1>
        </div>
        <!-- form -->
        <div class="form">
          <input type="text" placeholder="New Task" v-model="inputValue"/>
          <button  @click="$emit('addTask', inputValue)"><i class="fas fa-plus"></i></button>
        </div>
        <!-- task lists -->
        <div class="taskItems">
            <ul>
            <li v-for="task of props.tasks.filter(t => t.completed)">
              <button><span>
                <i  class="fa-solid fa-check"></i>
               </span>
                {{ task.title }}</button>
              <button @click="$emit('deleteTask', task.id)"><i class="far fa-trash-alt"></i></button>
            </li>
          </ul>
        </div>
        <!-- buttons --> 
        <div class="clearBtns">
          <button @click="$emit('clearCompletedTasks')">Clear completed</button>
          <button @click="$emit('clearAllTasks')">Clear all</button>
        </div>
        <!-- pending task -->
        <div class="taskItems">
          <span class="pendingTask">Pending Tasks: </span>
          <ul>
            <li v-for="task of props.tasks.filter((task,index) => !task.completed)">
             <button>
                <span><i class="fa-solid fa-hourglass-start"></i></span>
                {{ task.title }}
             </button>
             <div class="taskItems-actions">
                <button  @click="$emit('finishTask', task)"><i  class="fa-solid fa-check"></i></button>
                <button   @click="$emit('deleteTask', task.id)"><i class="far fa-trash-alt"></i></button>
             </div>
            </li>
          </ul>
        </div>
        <p>{{ inputValue }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
     const inputValue = ref("")

     const props = defineProps({
      tasks: Array,
     })
    
  </script>
  