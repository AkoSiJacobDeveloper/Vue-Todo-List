<template>
  <div>
    <h2 class="text-white m-2">Todo List</h2>
    <div v-for="todo in todos" :key="todo.id">
      <ToDoItem 
        :todo="todo" 
        @remove-todo="removeTodo" 
        @edit-todo="editTodo" 
      />
    </div>
  </div>
</template>

<script>
import ToDoItem from './ToDoItem.vue';

export default {
  components: {
    ToDoItem,
  },
  props: {
    todos: Array,
  },
  methods: {
    removeTodo(todo) {
      this.$emit('remove-todo', todo);
    },
    editTodo(updatedTodo) {
      this.$emit('edit-todo', updatedTodo); // Emit the updated todo
    },
  },
};
</script>
