<template>
        <div class="todo-item" v-bind:class="{'is-complete' :todo.completed}">
                <input type="checkbox" v-on:change="checkComplete" class="checker">
                <span>{{ todo.title }}</span>
                <font-awesome-icon icon="trash-alt" @click="$emit('del-todo', todo.id)" class="delete"/>
                <!-- <button class="del" @click="$emit('del-todo', todo.id)">X</button> -->
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
                text-align: left;
                margin: 7px;
                padding: 15px;
                color: crimson;
                font-size: 14px;
                font-weight: 500;
                background: rgb(248, 245, 246);
                border-radius: 5px;
                cursor: pointer;
                transition:  all 0.5sec ease-in-out;
        }

        .todo-item:hover {
                background: rgb(247, 239, 240);
                /* color: rgb(231, 87, 116); */
        }

        .is-complete {
                text-decoration: line-through;
                color:rgb(221, 135, 152)
        }

        span {
                margin: 0px  20px;
        }

        .delete {
                float: right;
        }
        /* .del {
                float: right;
                color: #fff;
                background: crimson;
                border-radius: 50%;
                width: 20px;
                height: 20px;
                border: none;
        } */
</style>