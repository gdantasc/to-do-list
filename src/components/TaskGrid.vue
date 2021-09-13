<template>
    <div class="task-grid">
        <template>
            <Task v-for="(task, i) in tasks" :key="task.name"
            @taskDeleted="$emit('taskDeleted', i)"
            @taskStateChanged="$emit('taskStateChanged', i)"
             :task="task"></Task>
        </template>
    </div>
  
</template>

<script>
import Task from "./Task.vue"
export default {
    components: {Task},
    props:{
        tasks: {type: Array, required: true}
    }
}
</script>

<style>
    .task-grid {
        margin: auto;        
        justify-content:center;
        
    }

    .task-grid .task {
        margin: 10px auto;
    }
</style>