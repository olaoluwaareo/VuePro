<template>
  <div id="app">
    <h1>Vue Todo List</h1>
    <form @submit.prevent="addTodo">
      <input v-model="newTodo" placeholder="Add a todo" />
      <button type="submit">Add</button>
    </form>
    <ul>
      <TodoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        @toggle="toggleTodo"
        @delete-todo="deleteTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';

export default {
  components: {
    TodoItem,
  },
  data() {
    return {
      newTodo: '',
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim()) {
        this.todos.push({
          text: this.newTodo,
          completed: false,
        });
        this.newTodo = '';
      }
    },
    toggleTodo(todo) {
      todo.completed = !todo.completed;
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((t) => t !== todo);
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 50px;
}
</style>
