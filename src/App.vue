<template>
    <div id="app">
        <div class="header">
            <img width="185" src="./assets/images/logo.svg" alt="Smartfit logo">
        </div>
    </div>
</template>

<script>
import SearchUnits from './components/SearchUnits.vue'
import Units from './components/Units.vue'

export default {
    name: 'App',
    components: {
      
    }
}
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

.header {
    width: 100%;
    text-align: center;
    padding: 26px;
    background-color: #000000;
}
</style>
