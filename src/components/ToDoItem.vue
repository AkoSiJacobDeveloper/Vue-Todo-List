<template>
  <div>
    <input type="checkbox" v-model="todo.completed" />
    <span v-if="!isEditing" :class="{ completed: todo.completed }">{{ todo.text }}</span>
    <input v-if="isEditing" v-model="editedText" />
    <button @click="removeTodo">Delete</button>
    <button v-if="!isEditing" @click="editTodo">Edit</button>
    <button v-if="isEditing" @click="saveEdit">Save</button>
  </div>
</template>

<script>
export default {
  props: {
    todo: Object,
  },
  data() {
    return {
      isEditing: false,
      editedText: this.todo.text, // Initialize with current todo text
    };
  },
  methods: {
    removeTodo() {
      this.$emit('remove-todo', this.todo);
    },
    editTodo() {
      this.isEditing = true; // Enable editing mode
      this.editedText = this.todo.text; // Set input field to current text
    },
    saveEdit() {
      if (this.editedText.trim()) {
        this.$emit('edit-todo', { ...this.todo, text: this.editedText }); // Emit the edited todo
        this.isEditing = false; // Exit editing mode
      }
    },
  },
};
</script>

<style>
.completed {
  text-decoration: line-through;
}
</style>
