<template>
        <div>
                <form @submit="addTodo">
                        <input type="text" name="title" placeholder="Add Todo..."  class="txtbox" v-model="title">
                        <input type="submit" value="Add" class="btn">
                </form>
        </div>
</template>


<script>

// import {v4 as uuidv4 } from 'uuid';

export default {
        name: 'AddTodo',
        data() {
                return {
                        title: ''
                }
        },

        methods: {
                addTodo(e) {
                        e.preventDefault()
                        const newTodo = {
                                // id: uuidv4(),
                                title: this.title,
                                completed: false
                        }
                        // Sending emit s   ignal to parent
                        this.$emit('add-todo', newTodo)

                        this.title = ' ';
                }
        }
}
</script>

<style scoped>
        form {
                text-align: center;
        }

        .txtbox {
                border: none;
                width: 200px;
                height: 30px;
                border-radius: 4px;
                background-color: rgb(248, 245, 246);
                padding: 4px  20px;
        }

        .btn {
                margin: 10px;
                border: none;
                width: 70px;
                height: 37px;
                border-radius: 4px;
                color: #fff;
                background-color: crimson;
                cursor: pointer;
                transition: all 0.3s ease-in-out;
        }

        ::placeholder {
                color: rgb(219, 146, 160)
        }

        .btn:hover {
                background-color: rgb(220, 20, 60, 0.8);
        }

        input[type="submit"] {
                margin: 10px
        }
</style>