<template>
    <div class="container">
      <div class="task">
        <!-- title -->
        <div class="title">
          <h1>To Do List</h1>
        </div>
        <!-- form -->
        <div class="form">
          <input type="text" placeholder="New Task" v-model="inputValue" />
          <button><i class="fas fa-plus"></i></button>
        </div>
        <!-- task lists -->
        <div class="taskItems">
            <ul>
            <li v-for="task of tasks.filter(t => t.completed)">
              <button><span>
                <i  class="fa-solid fa-check"></i>
               </span>
                {{ task.title }}</button>
              <button><i class="far fa-trash-alt"></i></button>
            </li>
          </ul>
        </div>
        <!-- buttons --> 
        <div class="clearBtns">
          <button>Clear completed</button>
          <button>Clear all</button>
        </div>
        <!-- pending task -->
        <div class="taskItems">
          <span>Pending Tasks: </span>
          <ul>
            <li v-for="task of tasks.filter(t => !t.completed)">
             <button>
                <span><i class="fa-solid fa-hourglass-start"></i></span>
                {{ task.title }}
             </button>
                <button><i class="far fa-trash-alt"></i></button>
            </li>
          </ul>
        </div>
        <p>{{ inputValue }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
    //  const  name = ref("Task");
     const inputValue = ref("")

     const props = defineProps({
      tasks: Array,
     })
    
     const {tasks} = props

     function addTask(task) {
        tasks.push(task)
     }
  
  </script>
  