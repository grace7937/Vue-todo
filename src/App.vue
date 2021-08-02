<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo App</h1>
    <input 
      type="text" 
      class="w-100 p-2" 
      placeholder="type todo"
      @keyup.enter="addTodo"
      >
      
  <hr>
  <Todo :todos="todos" v-for="(todo, index) in todos" :key="index" :todo="todo"/>
    
  </div>
</template>

<script>

import Todo from "../src/components/Toto.vue";
export default {
  components: {
    Todo
  },
  data() {
    return {
      todos: [
        { id: 1 , text: 'buy a 1', checked: false },
      ]
    }
  },

  methods: {
    addTodo(e) {
      const todoText = e.target.value;
      const todo = { id: Math.random , text: todoText, checked: false }
      this.todos.push(todo);

      e.target.value = "";
    },
    removeTodo(e) {
      todos.map((todo) => {
        
      })
    }
  }
  
}
</script>

