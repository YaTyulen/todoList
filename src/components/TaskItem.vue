<script setup>
import IconBase from './IconBase.vue';
import DeleteIcon from './icons/DeleteIcon.vue';
defineProps({
    task: Object,
})

defineEmits(['toggle-task', 'delete-task'])
</script>

<template>
    <li class="task-item" :key="task.id">
        <div class="task-name-container">
            <input type="checkbox" :checked="task.done" @change="$emit('toggle-task', task.id);">
            <span class="task-text">{{ task.text }}</span>
        </div>
        <button @click="$emit('delete-task', task.id);" class="task-delete-button">
            <IconBase width="12" height="12" iconColor="blue"><DeleteIcon /></IconBase>
        </button>
    </li>

</template>

<style scoped>
.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-right: 2px;
}

.task-item:hover {
   background-color: var(--backgroundButtonsActive);
}

input:checked ~ .task-text {
    text-decoration: line-through;
}

.task-name-container {
    display: flex;
    gap: 10px;
}

.task-delete-button {
    background-color: var(--baseWhiteColor);
    border: 2px solid var(--deleteColor);
    color: var(--deleteColor);
    border-radius: 3px;
    padding: 3px 5px;
}

.task-delete-button:hover {
    border-color: #820000;
    color: #820000;
    cursor: pointer;
}

.task-delete-button:active {
    background-color: var(--backgroundButtonsActive);
}
</style>