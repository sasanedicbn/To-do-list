<template>
   <input type="text" placeholder="New Task" v-model="inputValue"/>
</template>

<script setup>
const props = defineProps({
    task: Object;
})
</script>