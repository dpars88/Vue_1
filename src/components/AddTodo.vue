<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model ="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
//import { v4 as uuidv4 } from 'uuid'; not needed anymore due to API not needing uuid

export default {
    name: "AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                //id: uuidv4(), ----- removed due to note in above import line
                title: this.title,
                completed: false
            }
            //send up to parent by emitting event
            this.$emit('add-todo', newTodo)

            //remove what was entered in addTodo space after submitting
            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>