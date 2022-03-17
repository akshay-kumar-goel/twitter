<template>
<div id="app">
    <UserProfile />
</div>
</template>

<script>
import UserProfile from './components/UserProfile.vue'

export default {
    name: 'App',
    components: {
        UserProfile
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    min-height: 100vh;
    background-color: #f3f5FA;
}
</style>

 <!-- color: #2c3e50;
    display: flex;
    flex-direction: column;
    text-align: center; -->
