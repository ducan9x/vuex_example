<template>
    <div class="todo-list">
        <ul v-if="isAuthenticated">
            <TodoForm />
            <li
                v-for="todo in todos"
                :key="todo.id"
                :class="todo.completed ? 'completed' : ''"
            >
                {{ todo.title }}
                <input
                    type="checkbox"
                    :checked="todo.completed"
                    @change="MARK_COMPLETE(todo.id)"
                />
                <button @click="deleteTodo(todo.id)">Delete</button>
            </li>
        </ul>
        <p v-else style="text-align: center">Not authorised</p>
    </div>
</template>

<script>
import { mapActions, mapGetters, mapMutations } from 'vuex';
import TodoForm from './TodoForm';
export default {
    name: 'Todos',
    computed: mapGetters(['isAuthenticated', 'todos']),
    created() {
        this.getTodos();
    },
    methods: {
        ...mapMutations(['MARK_COMPLETE']),
        // deleteTodo(todoId){
        //     this.$store.dispatch('deleteTodo',todoId)
        // }
        ...mapActions(['deleteTodo', 'getTodos']),
    },
    components: {
        TodoForm,
    },
};
</script>

<style>
.todo-list {
    display: flex;
    justify-content: center;
}
.todo-list ul {
    width: 100%;
    padding: 0 10px 10px 10px;
    list-style-type: none;
    display: flex;
    flex-direction: column;
}
.todo-list li {
    padding: 10px;
    cursor: pointer;
    margin: 10px 0;
    border-radius: 4px;
    background: white;
    color: black;
}
.todo-list li.completed {
    background-color: rgb(124, 231, 16);
}
input {
    float: right;
}
.todo-list li button {
    float: right;
    margin-right: 20px;
}
.todo-list li button:hover {
    cursor: pointer;
    background: red;
    color: white;
}
</style>
