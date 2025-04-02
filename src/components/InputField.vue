<script setup>
let taskValue = '';
defineProps({
    value: String,
})

function addTask() {
    console.log(taskValue);
    if (taskValue.trim()) {
        const newTask = {
            id: Date.now(),
            text: taskValue,
            done: false
        }

        this.$emit('addTask', taskValue);
    }
}


</script>

<template>
    <input v-model="taskValue" />
    <button @click="addTofo()">Добавить</button>
</template>

<style scoped></style>