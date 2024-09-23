<script setup>
import { ref } from 'vue';

const task= ref('')

const Lists = ref([]);


const fetchTodoList = () => {
  const savedTodoList=JSON.parse(localStorage.getItem('Lists'));
  if (savedTodoList) {
    Lists.value = savedTodoList;
  }
}

fetchTodoList();


const setTodoListLocalStorege = () => {
    localStorage.setItem('Lists', JSON.stringify(Lists.value));

}
  


 


const createTodo = () => {

Lists.value.push(task.value)
localStorage.setItem('Lists', JSON.stringify(Lists.value));

    task.value = ''


}




const remove = (index) => {

    Lists.value.splice(index, 1)
    localStorage.setItem('Lists', JSON.stringify(Lists.value));

}







</script>

<template>
  <div class="todo-app">
    <h1 class="app-title">Todolist</h1>

    <div class="task-input">
        <input v-model="task" class="task-input" type="text" name="" id="" @keyup.enter="createTodo">

 <button @click="createTodo">creat</button>

    </div>


<div class="task-list">

    <ul >
    <li class="task-item" v-for="(ta,i) in Lists" :key="i" >
        {{ta}} 
        <button class="remove-button" @click="remove(i)">remove</button>
    </li>

</ul>


</div>


  </div>



</template>



<style scoped>
.todo-app {
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.app-title {
  font-size: 24px;
  margin-bottom: 20px;
  text-align: center;
  color: #333;
}

.task-input {
  display: flex;
  gap: 10px;
}

input {
  flex: 1;
  padding: 8px;
  font-size: 14px;
}

button {
  padding: 8px 12px;
  font-size: 14px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

.task-list {
  list-style: none;
  padding: 0;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  margin: 8px 0;
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.remove-button {
  padding: 6px 10px;
  font-size: 12px;
  background-color: #e74c3c;
  color: #fff;
  border: none;
  border-radius: 3px;
  cursor: pointer;
}

.remove-button:hover {
  background-color: #c0392b;
}
</style>