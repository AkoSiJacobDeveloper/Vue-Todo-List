<template>
    <header class="w-50">
        <h6 class="fw-bold text-center text-white">{{ title }}</h6>
        <p class="text-description fs-4 text-white"> 
            This project is a straightforward yet efficient task management tool built with <strong>Vue.js</strong> for interactivity, <strong>HTML</strong> for structure, <strong>SCSS</strong> for styling, and <strong>Bootstrap5</strong> for responsiveness. The app allows users to add task, edit, delete, and mark as complete, helping them to stay organized and productive.  
        </p>
    </header>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    setup() {
        return {
            title: 'To-Do List', 
        };
    }
});
</script>

<style lang="scss" scoped>
@import '@/assets/Styles/Styles.scss';
header {
    h6 {
        font-size: 5em;
    }
    
    .text-description {
        text-align: justify;
        font-family: $secondary-font;
    }

    

}
</style>
