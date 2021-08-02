<template>
  <div>
    <input type="checkbox" :checked="todo.checked" />
    <span class="ml-3">{{ todo.text }}</span>
    <span><button @click="removeTodo">X</button></span>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
    todos: {
      type: Array,
      required: false,
    },
  },
  methods: {
    removeTodo(e) {
      const filterdTodos = this.todos.filter((todo) => {
        return e.target.value !== todo.text;
      });
      console.log(filterdTodos);
      this.todos = filterdTodos;
    },
  },
};
</script>

<style>
</style>