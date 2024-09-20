<template>
    <header>
        <h1 class="fw-bold text-center text-white">{{ title }}</h1>
    </header>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    setup() {
        return {
            title: 'Vue Todo App', 
        };
    }
});
</script>
