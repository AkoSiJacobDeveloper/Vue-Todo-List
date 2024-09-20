<template>
  <div id="app">
      <div class="container d-flex justify-content-center align-items-center vh-100">
        <div class="todo-wrapper p-3 d-flex justify-content-center align-items-center flex-column">
             <div class="wrapper w-100">
                <ToDoHeader />
                <ToDoInput @add-todo="addTodo" />
              </div>
              <div class="list-container w-100 border-light">
                <ToDoList :todos="todos" @remove-todo="removeTodo" @edit-todo="editTodo" class="text-center" />
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import ToDoHeader from './components/ToDoHeader.vue';
import ToDoInput from './components/ToDoInput.vue';
import ToDoList from './components/ToDoList.vue';

export default {
  components: {
    ToDoInput,
    ToDoList,
    ToDoHeader,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(todoText) {
      const newTodo = {
        id: Date.now(),
        text: todoText,
        completed: false,
      };
      this.todos.push(newTodo);
    },
    removeTodo(todo) {
      this.todos = this.todos.filter(t => t.id !== todo.id);
    },
    editTodo(updatedTodo) {
      const index = this.todos.findIndex(t => t.id === updatedTodo.id);
      if (index !== -1) {
        this.todos.splice(index, 1, updatedTodo); // Replace the old todo with the updated one
      }
    },
  },
};
</script>

<style lang="scss">
@import './assets/Styles/Styles.scss';

#app {
  background-image: url(/wave.svg);
  background-size: cover;
  background-position: center;
  height: 100vh;

  div {
    box-sizing: border-box;

    .todo-wrapper {
      height: 80vh;
      width: 50vw;
      border: 1px solid black;
      padding: 20px; // Ensure there's space inside
      background: rgba(255, 255, 255, 0.2);
      border-radius: 16px;
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(5px);
      -webkit-backdrop-filter: blur(5px);   
      border: 1px solid rgba(255, 255, 255, 1);

      .wrapper {
        margin-bottom: 10px;
      }

      .list-container {
        border: 1px solid black;
        width: 100%;
        min-height: 60vh; // Make sure the container has height
      }
    }
  }
}

</style>
