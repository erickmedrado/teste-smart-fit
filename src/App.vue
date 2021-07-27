<template>
    <div id="app">
        <header>
            <img width="185" src="./assets/images/logo.svg" alt="Smartfit logo">
        </header>
        <div class="container">
            <div class="header">
                <h1>REABERTURA</h1>
                <h1>SMART FIT</h1>
                <hr>
                <p>O horário de funcionamento das nossas unidades está seguindo os decretos de cada município. Por isso, confira aqui se a sua unidade está aberta e as medidas de segurança que estamos seguindo.</p>
            </div>
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
@import '/assets/styles/main.css';

#app {
    color: #333333;
    font-weight: normal;
    font-family: "Gotham", sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

h1 {
    font-size: 41px;
    font-size: 2.57rem;
    line-height: 49.6rem;
    line-height: 3.1rem;
    font-family: "Gotham", sans-serif;
    font-weight: bolder;
}

header {
    width: 100%;
    text-align: center;
    padding: 26px 0;
    background-color: #000000;
}

.container {
    padding: 80px 0;
    margin: 0 auto;
    max-width: 920px;

}

.header {
    width: 100%;
}
</style>
