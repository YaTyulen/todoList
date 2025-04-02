<script setup>
import { ref } from 'vue'
import TaskList from './TaskList.vue';
import InputField from './InputField.vue';

let todoList = [
    { id: 1, text: 'Выполнить домашку', done: false },
    { id: 2, text: 'Написать диплом', done: true },
    { id: 3, text: 'Захватить мир', done: false }
];

function addTask(newTask) {
    todoList.push(newTask)
}

</script>

<template>
    <div>
        <h1>Список дел</h1>
        <InputField @addTask="addTask" />
        <TaskList :todoList="todoList" />
    </div>

</template>

<style scoped></style>