<script setup>
import IconBase from './IconBase.vue';
import DeleteIcon from './icons/DeleteIcon.vue';
import { ref } from 'vue'
const props = defineProps({
    task: Object,
})

const localTask = ref(props.task)
const edit = ref(false);
const currentTextTask = ref('')

const editModeSwitch = () => {
    edit.value = true
    currentTextTask.value = props.task.text
}

const editTask = () => {
    edit.value = false;
    if (currentTextTask.value.trim() && currentTextTask.value !== props.task.text) {
    emit('edit-task', {
      id: props.task.id,
      text: currentTextTask.value.trim()
    })
  }
    localTask.value = currentTextTask.value
}

const emit = defineEmits(['toggle-task', 'delete-task', 'edit-task'])
</script>

<template>
    <li :key="task.id">
        <div v-if="!edit" @dblclick="editModeSwitch" class="task-item">
            <div class="task-name-container">
                <input type="checkbox" :checked="task.done" @change="$emit('toggle-task', task.id);">
                <span class="task-text">{{ task.text }}</span>
            </div>
            <button @click="$emit('delete-task', task.id);" class="task-delete-button">
                <IconBase width="12" height="12" iconColor="blue"><DeleteIcon /></IconBase>
            </button>
        </div>
        <div v-else class="task-item task-item-edit">
            <input v-model="currentTextTask" @keyup.enter="editTask" type="text" class="edit-input">
            <button @click="editTask" class="save-edit-task">Сохранить</button>
        </div>
    </li>
</template>

<style scoped>
.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-right: 2px;
}

.task-item-edit {
    gap: 10px;
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

.edit-input {
    width: 100%;
    display: block;
    height: 30px;
    padding: 5px;
    border-radius: 3px;
    border: 2px solid var(--fontBaseColor)
}

.save-edit-task {
    background-color: var(--baseWhiteColor);
    border: 2px solid var(--addColor);
    border-radius: 3px;
    color: var(--addColor);
    padding: 5px;
}

.save-edit-task:hover {
    border-color: var(--addHoverColor);
    color: var(--addHoverColor);
    cursor: pointer;
}

.save-edit-task:active {
    background-color: var(--backgroundButtonsActive);
}
</style>