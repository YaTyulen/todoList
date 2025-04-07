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
    border: 2px solid #919191
}

.button-add {
    background-color: #ffffff;
    border: 2px solid #00ff99;
    border-radius: 3px;
    color: #00ff99;
}

.button-add:hover {
    border-color: #03b16b;
    color: #03b16b;
    cursor: pointer;
}

.button-add:active {
    background-color: #e4e4e4;
}
</style>