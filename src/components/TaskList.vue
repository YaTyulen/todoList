<script setup>
import TaskItem from './TaskItem.vue';
defineProps({
    taskList: Array,
})

defineEmits(['toggle-task', 'delete-task'])
</script>

<template>
    <ul class="task-list">
        <TaskItem 
            v-for="task in taskList" 
            :task="task" 
            :key="task.id" 
            @toggle-task="$emit('toggle-task', $event)" 
            @delete-task="$emit('delete-task', $event)"/>
    </ul>
</template>

<style scoped>
.task-list {
    margin: 0;
    padding: 0;
    list-style-type: none;
    display: flex;
    flex-direction: column;
    gap: 10px;
    font-size: 20px;
    max-height: 500px;
    overflow-y: auto;
}

.task-list::-webkit-scrollbar {
  width: 5px;               /* ширина scrollbar */
}

.task-list::-webkit-scrollbar-track {
  background-color: transparent;        /* цвет дорожки */
}
.task-list::-webkit-scrollbar-thumb {
  background-color: rgb(186, 186, 186);    /* цвет плашки */
  border-radius: 20px;       /* закругления плашки */
}
</style>
