<template>
        <div class="todo-item" v-bind:class="{'is-complete' :todo.completed}">
                <input type="checkbox" v-on:change="checkComplete" class="checker">
                <p>{{ todo.title }}</p>
                <button class="del" @click="$emit('del-todo', todo.id)">X</button>
        </div>
</template>


<script>


export default {
        name: 'TodoItems',
        props: ['todo'],
        methods: {
                checkComplete() {
                        this.todo.completed = !this.todo.completed;
                }
        }
}
</script>

<style scoped>
        .todo-item {
                color: crimson;
                margin: 5px;
                font-size: 14px;
                font-weight: 500;
                background: rgb(248, 245, 246);
                padding: 1px 5px 3px;
                border-radius: 5px;
                cursor: pointer;
                transition:  all 0.5sec ease-in-out;
        }

        .todo-item:hover {
                background: rgb(247, 239, 240);
                color: rgb(231, 87, 116);
        }

        .is-complete {
                text-decoration: line-through;
        }

        .del {
                color: #fff;
                background: crimson;
                border-radius: 50%;
                width: 20px;
                height: 20px;
                border: none;
        }
</style>