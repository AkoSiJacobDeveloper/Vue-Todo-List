<template>
  <div id="app">
    <div class="container d-flex justify-content-center align-items-center vh-100 gap-5">
      <ToDoHeader />
      <div class="todo-wrapper py-4 d-flex justify-content-center align-items-center flex-column">
        <div class="wrapper w-100">
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
        this.todos.splice(index, 1, updatedTodo);
      }
    },
  },
};
</script>

<style lang="scss">
@import './assets/Styles/Styles.scss';

#app {
  background-image: url(public/slanted-gradient.svg);
  background-position: center;
  background-size: cover;

  div {
    box-sizing: border-box;

    .todo-wrapper {
      height: 90vh;
      width: 50vw;
      padding: 20px;
      background: rgba(255, 255, 255, 0.2);
      border-radius: 10px;
      box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
      backdrop-filter: blur(15px);
      -webkit-backdrop-filter: blur(5px);  

      .wrapper {
        margin-bottom: 10px;
      }

      .list-container {
        height: 90%;
      }
    }
  }
}

</style>
