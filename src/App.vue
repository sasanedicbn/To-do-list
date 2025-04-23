<template>
  <div id="app">
    <Task 
      :tasks="tasks" 
      @deleteTask="deleteTask" 
      @addTask="addTask" 
      @finishTask="finishTask"
      @clearCompletedTasks="clearCompletedTasks"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Task from './components/Task.vue';

const tasks = ref([
  {
    id: 1,
    title: "Learn Vue JS",
    completed: true,
  },
  {
    id: 2,
    title: "Watch netflix",
    completed: true,
  },
  {
    id: 3,
    title: "Go shopping",
    completed: false,
  },
  {
    id: 4,
    title: "Learn guitar",
    completed: false,
  },
  {
    id: 5,
    title: "Send email",
    completed: false,
  },
]);

const deleteTask = (id) => {
  console.log(id, 'id', typeof(id))
  tasks.value = tasks.value.filter(task => task.id !== id);
  console.log(tasks.value, 'nakon')
};

const addTask = (inputValue) => {
  if(!inputValue.trim()) return;

  const newTask = {
    id: Math.random(),
    title: inputValue,
    completed: false,
  };

  tasks.value.push(newTask);
};

const finishTask = (task) => {
  const index = tasks.value.findIndex(t => t.id === task.id);
  if (index !== -1) {
    tasks.value[index].completed = true;
  }
};

const clearCompletedTasks = () => {
  tasks.value = []
}
</script>