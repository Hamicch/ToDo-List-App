<template>
        <div class="todos">
                <div v-for="todo in todos" :key="todo.id">
                <TodoItems v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
        </div>
        </div>
</template>


<script>

import TodoItems from './TodoItems'

export default {
        name: 'Todos',
        components: {
                TodoItems
        },
        props: ['todos']
}
</script>

<style scoped>
        .todos {
                margin-top: 50px;
        }
</style>