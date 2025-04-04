<script setup>
import { ref } from 'vue'
import TaskList from './TaskList.vue';
import InputField from './InputField.vue';

let countTask = 3
let todoList = ref([
    { id: 1, text: 'Выполнить домашку', done: false },
    { id: 2, text: 'Написать диплом', done: true },
    { id: 3, text: 'Захватить мир', done: false }
])

function addTask(newTask) {
    newTask && todoList.value.push({ id: countTask += 1, text: newTask, done: false })
}

</script>

<template>
    <div class="home-container">
        <h1>Список дел</h1>
        <div>
            <InputField @click="addTask" />
        </div>
        <TaskList :todoList="todoList" />
    </div>

</template>

<style scoped>
.home-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    padding: 20px;
}
</style>