<template>
  <div class="row justify-content-around">
    <div class="col-12 col-lg-10 col-xl-8 px-3">
      <table class="table table-striped table-hover table-bordered">
        <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Text</th>
          <th scope="col" style="width: 50px;">Status</th>
          <th scope="col" style="width: 250px;">Command</th>
        </tr>
        </thead>
        <tbody class="table-group-divider">
        <tr v-for="(todo, index) in todos">
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ todo.text }}</td>
          <td>{{ todo.done }}</td>
          <td>
            <button class="btn btn-sm btn-primary mx-1" @click="$emit('done-todo', index)">Done/Undone</button>
            <button class="btn btn-sm btn-danger mx-1" @click="$emit('delete-todo', index)">Delete</button>
            <button class="btn btn-sm btn-warning mx-1" @click="$emit('edit-todo', index)">Edit</button>
          </td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoList",
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
  ]
}
</script>

<style scoped>

</style>