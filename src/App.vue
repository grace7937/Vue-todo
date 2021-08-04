<template>
  <div id="app" class="container">
    <h1 class="text-center">Todo App</h1>
    <input 
      v-model="todoInputText"
      type="text" 
      class="w-100 p-2" 
      placeholder="type todo"
      @keyup.enter="addTodo"
      >
      
  <hr>
  <Todo :todos="todos" v-for="(todo, index) in todos" :key="index" :todo="todo" @toggle-checkbox="toggleCheckbox" @remove-todo="removeTodo"/>
    
  </div>
</template>

<script>

import Todo from "./components/Todo.vue";
export default {
  components: {
    Todo
  },
  data() {
    return {
      todoInputText:'',
      todos: [
      
      ]
    }
  },

  methods: {
    addTodo(e) {
      const todoText = e.target.value;
      const todo = { id: this.todos.length === 0 ? 1 : this.todos[this.todos.length - 1].id + 1 , text: todoText, checked: false }
      this.todos = [...this.todos, todo];                 // ...문법을 이용해 add

      this.todoInputText = "";
    },
    removeTodo(id) {
      const index = this.todos.findIndex(todo => {
        return todo.id === id;
      });
      this.todos.splice(index, 1);                       //splice를 이용해 remove
    },
    toggleCheckbox({id, checked}) {
      console.log(id,checked);
     const index = this.todos.findIndex(todo => {
       return todo.id === id;
     });
     this.todos[index].checked = checked;

    }
  }
  
}
</script>

