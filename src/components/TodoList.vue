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
        <Todo v-for="(todo, index) in todos.value" :index="index" :todo="todo"></Todo>
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
  inject: [
      'todos',
  ],
}
</script>

<style scoped>

</style>