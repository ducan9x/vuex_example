<template>
    <p class="progressbar" v-if="isAuthenticated">Progress {{ progress }}%</p>
</template>

<script>
import { mapGetters } from 'vuex';
export default {
    name: 'ProgressBar',
    computed: mapGetters(['progress', 'isAuthenticated']),
};
</script>

<style></style>
