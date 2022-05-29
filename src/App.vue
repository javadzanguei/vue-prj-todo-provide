<template>
  <header>
    <nav class="navbar bg-light">
      <div class="container-fluid">
        <span class="navbar-brand mb-0 h1">Todo</span>
      </div>
    </nav>
    <h1 class="text-lg text-center text-light bg-dark py-5">
      Todo App
    </h1>
  </header>
  <main>
    <CreateTodo class="py-5" @add-todo="addTodo"/>
    <hr>
    <TodoList :todos="todos" @done-todo="doneTodo" @edit-todo="editTodo" @delete-todo="deleteTodo"/>
  </main>
</template>

<style>
main {
  overflow: hidden;
}
</style>

<script>
import CreateTodo from "./components/CreateTodo.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    CreateTodo,
    TodoList
  },
  data() {
    return {
      todos: [
        {
          text: 'Call students',
          done: false,
        },
        {
          text: 'Call Teacher',
          done: false,
        }
      ]
    }
  },
  methods: {
    addTodo(newTodoText) {
      this.todos[this.todos.length] = {
        text: newTodoText,
        done: false,
      };
    },
    doneTodo(todoIndex) {
      this.todos[todoIndex].done = !this.todos[todoIndex].done;
    },
    deleteTodo(todoIndex) {
      this.todos = this.todos.filter((todo, index) => index !== todoIndex);
    },
    editTodo(todoIndex) {

    },
  }
}
</script>
