<template>
  <div id="app">
    <Task :tasks="tasks" @deleteTask="deleteTask"></Task>
  </div>
</template>

<script>
import Task from './components/Task.vue';


export default {
  name: "App",
  components: {
    Task,
  },
  methods:{
    deleteTask(id){
      tasks.filter((task, _) => task.id !== id)
   }
  },
  data() {
    return {
      tasks: [
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
      ],
    };
  },
};
</script>