<script setup>
import { ref } from 'vue'
import TaskList from './components/TaskList.vue';
import InputField from './components/InputField.vue';

let taskListLocalStorage = JSON.parse(localStorage.getItem('taskList')) // список задач из LocalStorage 
let countTask = taskListLocalStorage.length ?? 0 // id последней задачи
const taskList = ref([]) // отслеживаемая переменная со списком дел
if(taskListLocalStorage) {
    //если есть значение в localStorage
    taskList.value = taskListLocalStorage;
} else {
    // если нет, то добавляем пустой массив в localStorage
    localStorage.setItem('taskList', [])
}

// Функция добавления задачи
const addTask = (newTask) => {
    newTask && taskList.value.push({ id: countTask += 1, text: newTask, done: false })
    localStorage.setItem('taskList', JSON.stringify(taskList.value))
}

// Функция изменения состояния задачи (выполнено/не выполнено)
const toggleTask = (id) => {
    const task = taskList.value.find(item => item.id === id)
    if(task) {
        task.done = !task.done
    }
    localStorage.setItem('taskList', JSON.stringify(taskList.value))
}

// Функция удаления задачи
const deleteTask = (id) => {
    taskList.value = taskList.value.filter(item => item.id !== id)
    localStorage.setItem('taskList', JSON.stringify(taskList.value))
}
</script>

<template>
    <div class="home-container">
        <div class="list-container">
            <h1>Список дел</h1>
            <div class="input-add-container">
                <InputField @add-task="addTask"/>
            </div>
            <TaskList :taskList="taskList" @toggle-task="toggleTask" @delete-task="deleteTask"/>
        </div>
    </div>
</template>

<style scoped>
.home-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
  height: 100vh;
}

.list-container {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 20px;
  background-color: var(--baseWhiteColor);
  border-radius: 3px;
  width: 80%;
  height: 80%;
}

h1 {
  border-bottom: 1px solid var(--fontBaseColor);
}

.input-add-container {
  display: flex;
  justify-content: space-between;
  gap: 10px;
}
</style>
