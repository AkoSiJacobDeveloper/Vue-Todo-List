<template>
  <div class="item-holder p-xl-4 mb-2 text-white rounded-1">
    <div class="d-flex justify-content-between">
      <div class="holderOne d-flex gap-2 m-0">
        <input class="mt-2" type="checkbox" v-model="todo.completed" />
        <p class="m-0 fs-5 mt-3" v-if="!isEditing" :class="{ completed: todo.completed }">{{ todo.text }}</p>
        <input class="w-100 rounded-1" v-if="isEditing" v-model="editedText" />
      </div>
      <div class="holderTwo d-flex gap-1">
        <button class="border-0 py-xl-3 px-xl-4 fw-bold text-white rounded-1 w-50 deleteBtn" @click="removeTodo">Delete</button>
        <button class="border-0 py-xl-3 px-xl-4 fw-bold text-white rounded-1 w-50 editBtn" v-if="!isEditing" @click="editTodo">Edit</button>
        <button class="border-0 py-xl-3 px-xl-4 fw-bold text-white rounded-1 w-50 saveBtn" v-if="isEditing" @click="saveEdit">Save</button>
      </div>
    </div>
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

<style lang="scss" scoped>
.item-holder {
  box-shadow: rgba(255, 255, 255, 1) 0px 0px 0px 1px, rgba(0, 0, 0, 0.02) 0px 1px 3px 0px;
  box-sizing: border-box;

  div {
    .holderOne {
      input {
        accent-color: crimson;
      }
    }

    .holderTwo {
      .deleteBtn {
        background-color: crimson;
      }
      .editBtn {
        background-color: #17a2b8;
      }
      .saveBtn {
        background-color: #28a745;
      }
    }
  }

  .completed {
    text-decoration: line-through;
  }
}
</style>