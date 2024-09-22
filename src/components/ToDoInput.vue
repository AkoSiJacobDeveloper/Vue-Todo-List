<template>
    <div class="d-flex gap-1 p-xl-4 rounded-1">
        <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new task" class="w-100 p-xl-4 rounded-1" />
        <button @click="addTodo" class="py-xl-3 px-xl-5 rounded-1 fw-bold border-none">Add</button>
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
div {
    box-shadow: rgba(255, 255, 255, 1) 0px 0px 0px 1px, rgba(0, 0, 0, 0.02) 0px 1px 3px 0px;
    box-sizing: border-box;

    input {
        border: none;
    }
    
    button {
       outline: none;
       background-color: #ffd700;
    }
}

</style>