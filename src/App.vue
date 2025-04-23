<template>
  <div id="app">
    <Task :tasks="tasks" @deleteTask="deleteTask" @addTask="addTask" @finishTask="finishTask" ></Task>
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
      console.log(id, 'id from child')
    //  this.tasks = this.tasks.splice((task, _) => task.id === id)
       this.$set(this, 'tasks', this.tasks.filter(task => task.id !== id));

    },
     addTask(inputValue) {
        if(!inputValue.trim()) return;

        const newTask = {
            id: Math.random(),
            title: inputValue,
            completed: false,
        }

        this.tasks.push(newTask)
        inputValue = '';
     },

     finishTask(task){
      const index =  this.tasks.findIndex(t => t.id === task.id)
      if (index !== -1) {
       this.tasks[index].completed = true
        }
     },
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