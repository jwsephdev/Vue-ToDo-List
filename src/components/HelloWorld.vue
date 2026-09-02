<script setup>

import { ref } from 'vue'

let id = 0;

const tasks = ref([
  {id: id++, message: 'Foo', done: false },
  {id: id++, message: 'Bar', done: true},
])
const inputText = ref('');


const addTask = () => {
  if (inputText.value.trim() != "")
{

  const newValue = {
    id: id++,
    message: inputText.value,
    done: false
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
      <li v-for="(task, index) in tasks" :key="index" style="display: flex; flex-direction: row; ">

        <input type="checkbox" v-model="task.done">

        <p :class="{done : task.done}" style="margin: 5px;">{{ task.message }}</p>

        <div style="display: flex; align-items: center; justify-content: center; margin: 5px;">
          <button @click="removeTask(task)" :class="taskBtn">x</button>
        </div>
        

      </li>
    </ul>
  </div>
  
  
</template>

<style>
  .done {
    text-decoration: line-through;
  }
  .taskBtn {
    width: fit-content;
    height: fit-content;
  }

</style>