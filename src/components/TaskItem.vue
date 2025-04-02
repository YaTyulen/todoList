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

<style scoped></style>
