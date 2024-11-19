<template>
    <div>
      <li :class="{ completed: todo.completed }">
        <input type="checkbox" @change="toggleTodo" :checked="todo.completed" /> 
        {{ todo.text }}
        <button @click="deleteTodo">Delete</button>
      </li>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true,
      },
    },
    methods: {
      toggleTodo() {
        this.$emit('toggle', this.todo);
      },
      deleteTodo() {
        this.$emit('delete-todo', this.todo);
      },
    },
  };
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }
  button {
    margin-left: 10px;
    color: red;
  }
  </style>
  