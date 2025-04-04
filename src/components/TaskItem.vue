<script setup>
defineProps({
    task: Object,
})
</script>

<template>
    <li class="task-item" :key="task.id">
        <input type="checkbox" :checked="task.done">
        <span>{{ task.text }}</span>
    </li>

</template>

<style scoped>
.task-item {
    display: flex;
    gap: 10px;
    align-items: center;
}
</style>