<script setup>

import { ref } from 'vue'


const tasks = ref([{message: 'Foo' }, { message: 'Bar' }])
const inputText = ref('');


const addTask = () => {
  if (inputText.value.trim() != "")
{

  const newValue = {
    message: inputText.value
  }
  tasks.value.push(newValue);

  inputText.value = '';
}

}

function removeTask(event)
{
  tasks.value = tasks.value.filter((t) => t !== event);
}

</script>



<template>
  <h1>Hello, World</h1>
  <h1>Todo List</h1>
  <div>
    <input v-model="inputText" placeholder="input task..">
    <button @click="addTask">Add</button>
  </div>

  <div>
    <ul>
      <li v-for="(task, index) in tasks" :key="index" style="display: flex;">
        <p>{{ task.message }}</p>
        <button @click="removeTask(task)">x</button>
      </li>
    </ul>
  </div>
  
  
</template>
