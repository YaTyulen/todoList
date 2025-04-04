<script setup>
import TaskItem from './TaskItem.vue';
defineProps({
    todoList: Array,
})
</script>

<template>
    <ul class="task-list">
        <TaskItem v-for="task in todoList" :task="task" />
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
}
</style>
