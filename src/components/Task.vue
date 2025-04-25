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
          <button  @click="handleAddTask"><i class="fas fa-plus"></i></button>
        </div>
        <!-- task lists -->
        <div class="taskItems">
            <ul v-if="hasCompletedTask" >
            <li v-for="task of competedTask">
              <button><span>
                <i  class="fa-solid fa-check"></i>
               </span>
                {{ task.title }}</button>
              <button @click="emit('deleteTask', task.id)"><i class="far fa-trash-alt"></i></button>
            </li>
          </ul>
          <p v-else class="no-more">No more completed task...</p>
        </div>
        <!-- buttons --> 
        <div class="clearBtns">
          <button @click="emit('clearCompletedTasks')">Clear completed</button>
          <button @click="emit('clearAllTasks')">Clear all</button>
        </div>
        <!-- pending task -->
        <div class="taskItems">
          <span class="pendingTask">Pending Tasks: </span>
          <ul v-if="hasPendingTask">
            <li v-for="task of pendingTask">
             <button>
                <span><i class="fa-solid fa-hourglass-start"></i></span>
                {{ task.title }}
             </button>
             <div class="taskItems-actions">
                <button  @click="emit('finishTask', task)"><i  class="fa-solid fa-check"></i></button>
                <button   @click="emit('deleteTask', task.id)"><i class="far fa-trash-alt"></i></button>
             </div>
            </li>
          </ul>
          <p v-else class="no-more">No more pending task...</p>
        </div>
        <p>{{ inputValue }}</p>
      </div>
    </div>
  </template>
  
  <script setup>
  import { computed, ref } from 'vue'
     const emit = defineEmits(['addTask', 'deleteTask', 'finishTask', 'clearAllTasks', 'clearCompletedTasks'])
     const inputValue = ref("")

     const props = defineProps({
      tasks: Array,
     })

     const competedTask = computed(() =>  props.tasks.filter(t => t.completed))
     const hasCompletedTask = computed(() =>  competedTask.value.length > 0)
     const pendingTask = computed(() => props.tasks.filter(t => !t.completed))
     const hasPendingTask = computed(() => pendingTask.value.length > 0)
    

     const handleAddTask = () => {
      if(!inputValue.value.trim()) return;

      emit("addTask", inputValue.value)

      inputValue.value = "";
      
     }
    
  </script>
  