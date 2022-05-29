<template>
  <div class="row justify-content-around">
    <div class="col-4">
      <form @submit.prevent>
        <div class="input-group mb-3">
          <input v-model="newTodoText" aria-describedby="button-addon2" aria-label="Todo text" class="form-control"
                 placeholder="Todo text" type="text" @keyup.enter="addTodo">
          <button id="button-addon2" class="btn btn-success" type="button" @click="addTodo">Add</button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "CreateTodo",
  data() {
    return {
      newTodoText: ''
    }
  },
  methods: {
    addTodo() {
      this.$emit('add-todo', this.newTodoText)
      this.newTodoText = ''
    }
  }
}
</script>

<style scoped>

</style>