<script setup>
let taskValue = '';
</script>

<template>
    <input v-model="taskValue" type="text" />
    <button class="button-add" @click="$emit('click', taskValue)" title="Добавить задачу">+</button>
</template>

<style scoped>
input {
    height: 30px;
    padding: 5px;
    border-radius: 5px;
    border: 2px solid #919191
}

.button-add {
    background-color: transparent;
    border: none;
}
</style>