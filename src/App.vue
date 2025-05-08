<template>
  <body>
    <div class="container">
      <section>
        <input type="text" class="input-group" v-model="inputTodo">
        <button @click="addTodo()" class="btn-success btn">Add</button>
      </section>

      <ul class="list-group" v-for="todo in todoList" key="todo.id"> 
        <li class="list-group-item" v-if="todo!=''">
          {{ todo }}
          <button @click="() => deleteTodo(todo)" class="btn btn-danger">Delete</button>
        </li>
      </ul>
    </div>
  </body>
</template>

<script setup lang="ts">
  import { ref, type Ref } from 'vue'
  
      const inputTodo: Ref<string> = ref('')
      const todoList: Ref<string[]> = ref([])
      

    
      function addTodo(){
        todoList.value.push(inputTodo.value)
        inputTodo.value = ""
      }
      

      function deleteTodo(todo: string){
        const index = todoList.value.indexOf(todo)
        if(index > -1){
          todoList.value.splice(1, index)
        }
      }
    

    
</script>

<style></style>

    