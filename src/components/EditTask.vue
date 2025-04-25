<template>
    <input
      type="text"
      placeholder="New Task"
      v-model="task.title"
    />
    <button @click="updateTaskHandler">
      <i class="fa-solid fa-check"></i>
    </button>
    <button>
      <i class="far fa-trash-alt"></i>
    </button>
  </template>
  
  <script setup>
  const emit = defineEmits(["updateTask"]);
  const props = defineProps({
    task: Object,
  });
  
  const updateTaskHandler = () => {
    emit("updateTask", props.task.title);
  };
  </script>
  