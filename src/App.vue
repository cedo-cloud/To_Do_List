<template>
    <div class="container" >

      <p><h1><center>To Do List </center></h1></p>
      <br></br>
      
      <section>
        <input type="text" class="input-group " placeholder="e.g. make a video" v-model="inputTodo">
        <button @click="addTodo()" class="btn-success btn">Add</button>
      </section>

      <ul class="list-group" v-for="todo in todoList" key="todo.id"> 
        <li class="list-group-item" v-if="todo!=''">
          {{ todo }}
          
          <button @click="deleteTodo(todo)" class="btn btn-danger"><i class="fa fa-trash" aria-hidden="true"></i>
            <!-- Add the style and icon you want using the Array format -->
            <font-awesome-icon :icon="['fas', 'trash']" />
          </button>
        </li>
      </ul>
    </div>
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
          todoList.value.splice(index, 1)
        }
      }
    

    
</script>

<style>
  
</style>

    

    
