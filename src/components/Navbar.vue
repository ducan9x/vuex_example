<template>
    <div class="navbar">
        <h1 class="heading">My Vuex App Todos</h1>
        <ul>
            <li>Home</li>
            <li>About</li>
            <li v-if="isAuthenticated">
                Total Todos: {{ todos.length }}
                <button @click="TOGGLE_AUTH">Logout</button>
            </li>
            <button @click="TOGGLE_AUTH" v-else>Login</button>
        </ul>
    </div>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex';

export default {
    name: 'Navbar',
    computed: mapGetters(['todos', 'isAuthenticated']),
    methods: mapMutations(['TOGGLE_AUTH']),
};
</script>

<style>
.navbar {
    padding: 5px;
    text-align: center;
    background: rgb(240, 240, 240);
    color: black;
}
.navbar ul {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    list-style: none;
    padding: 0;
}
</style>
