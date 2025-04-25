<template>
   <input type="text" placeholder="New Task" v-model="task.title"/>
   <button>submit</button>
</template>

<script setup>
const props = defineProps({
    task: Object,
})

console.log(props.task)
</script>