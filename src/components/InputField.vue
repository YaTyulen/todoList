<script setup>
import { ref } from 'vue'
const newTaskValue = ref('') // отслеживаемая переменная новой задачи

const emit = defineEmits(['add-task'])

// обработчик введения новой задачи
const handlerAddTask = () => {
    if (newTaskValue.value.trim()) {
        emit('add-task', newTaskValue.value);
        newTaskValue.value = '';
    }
}
</script>

<template>
    <input v-model="newTaskValue" @keyup.enter="handlerAddTask" class="input-add" type="text" placeholder="Напишите задачу"/>
    <button class="button-add" @click="handlerAddTask" title="Добавить задачу">Добавить</button>
</template>

<style scoped>
.input-add {
    width: 100%;
    display: block;
    height: 30px;
    padding: 5px;
    border-radius: 3px;
    border: 2px solid var(--fontBaseColor)
}

.button-add {
    background-color: var(--baseWhiteColor);
    border: 2px solid var(--addColor);
    border-radius: 3px;
    color: var(--addColor);
}

.button-add:hover {
    border-color: var(--addHoverColor);
    color: var(--addHoverColor);
    cursor: pointer;
}

.button-add:active {
    background-color: var(--backgroundButtonsActive);
}
</style>