<template>
  <tr>
    <th scope="row">{{ index + 1 }}</th>
    <td v-show="!editState" v-text="todo.text"></td>
    <td v-show="editState">
      <input v-model="editText" type="text" @keyup.enter="doneEdit">
    </td>
    <td>{{ todo.done }}</td>
    <td>
      <button v-show="!editState" class="btn btn-sm btn-primary mx-1" @click="$emit('done-todo', index)">Done/Undone
      </button>
      <button v-show="!editState" class="btn btn-sm btn-danger mx-1" @click="$emit('delete-todo', index)">Delete
      </button>
      <button v-show="!editState" class="btn btn-sm btn-warning mx-1" @click="editRow">Edit</button>
      <button v-show="editState" class="btn btn-sm btn-success mx-1" @click="doneEdit">Save</button>
      <button v-show="editState" class="btn btn-sm btn-secondary mx-1" @click="editState = false">Cancel</button>
    </td>
  </tr>
</template>

<script>
export default {
  name: "Todo",
  props: [
    'todo',
    'index'
  ],
  emits: [
    'done-todo',
    'delete-todo',
    'edit-todo',
  ],
  data() {
    return {
      editState: false,
      editText: '',
    }
  },
  methods: {
    editRow() {
      this.editState = true
      this.editText = this.todo.text
    },
    doneEdit() {
      this.editState = false
      this.todo.text = this.editText
      this.$emit('edit-todo', this.index, this.editText)
    }
  }
}
</script>

<style scoped>

</style>