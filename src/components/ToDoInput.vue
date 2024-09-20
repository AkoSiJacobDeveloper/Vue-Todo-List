<template>
    <div class="d-flex gap-1">
        <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task" class="w-100 p-3" />
        <button @click="addTodo" class="p-2 px-4">Add</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodo: '',
        };
    },
    methods: {
        addTodo() {
            if (this.newTodo.trim()) {
                this.$emit('add-todo', this.newTodo);
                this.newTodo = '';
            }
        },
    },
}
</script>

<style lang="scss" scoped>

input {
    border: none;
}

button {
   outline: none;
}
</style>