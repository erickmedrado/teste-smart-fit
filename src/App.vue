<template>
    <div id="app">
        <header>
            <img width="185" src="./assets/images/logo.svg" alt="Smartfit logo">
        </header>
        <div class="container">
            <div class="header">
                <h1>REABERTURA</h1>
                <h1>SMART FIT</h1>
                <hr class="headline">
                <p>O horário de funcionamento das nossas unidades está seguindo os decretos de cada município. Por isso, confira aqui se a sua unidade está aberta e as medidas de segurança que estamos seguindo.</p>
            </div>
            <FormSearch></FormSearch>
        </div>
    </div>
</template>

<script>
import FormSearch from './components/FormSearch.vue'
import Units from './components/Units.vue'

export default {
    name: 'App',
    components: {
        FormSearch,
        Units,
    }
}
</script>

<style>
@import '/assets/styles/main.css';

#app {
    color: #333;
    font-weight: normal;
    font-family: 'Gotham', sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

h1 {
    font-size: 41px;
    font-size: 2.57rem;
    line-height: 49.6rem;
    line-height: 3.1rem;
    font-family: 'Gotham Bold', sans-serif;
    font-weight: bolder;
}

p {
    font-size: 15.8px;
    font-size: 0.99rem;
    letter-spacing: 0px;
    line-height: 27px;
    line-height: 1.68rem;
    font-family: 'Gotham', sans-serif;
}

header {
    width: 100%;
    text-align: center;
    padding: 26px 0;
    background-color: #000;
}

.container {
    padding: 80px 0;
    margin: 0 auto;
    max-width: 920px;
}

.header .headline {
    width: 100px;
    height: 10px;
    border: none;
    margin: 20px auto 35px 0;
    background-color: #333;
}
</style>
