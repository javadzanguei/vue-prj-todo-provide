<template>
  <div class="row justify-content-around">
    <div class="col-12 col-lg-10 col-xl-8 px-3">
      <table class="table table-striped table-hover table-bordered">
        <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Text</th>
          <th scope="col" style="width: 50px;">Status</th>
          <th scope="col" style="width: 270px;">Command</th>
        </tr>
        </thead>
        <tbody class="table-group-divider">
        <Todo v-for="(todo, index) in todos" :index="index" :todo="todo"
              @done-todo="doneTodo" @edit-todo="editTodo" @delete-todo="deleteTodo"></Todo>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo.vue";
export default {
  name: "TodoList",
  components: {
    Todo
  },
  props: {
    todos: {
      type: Array,
      required: true,
    }
  },
  emits: [
    'done-todo',
    'delete-todo',
    'edit-todo',
  ],
  methods: {
    doneTodo(todoIndex) {
      this.$emit('done-todo', todoIndex);
    },
    deleteTodo(todoIndex) {
      this.$emit('delete-todo', todoIndex);
    },
    editTodo(todoIndex, todoText) {
      this.$emit('edit-todo', todoIndex, todoText);
    },
  }
}
</script>

<style scoped>

</style>