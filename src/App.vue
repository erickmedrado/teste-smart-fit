<template>
    <div id="app">
        <header>
            <img class="logo" src="./assets/images/logo.svg" alt="Smartfit logo">
        </header>
        <div class="container">
            <div class="header">
                <h1>REABERTURA</h1>
                <h1>SMART FIT</h1>
                <hr class="headline">
                <p>O horário de funcionamento das nossas unidades está seguindo os decretos de cada município. Por isso, confira aqui se a sua unidade está aberta e as medidas de segurança que estamos seguindo.</p>
            </div>
            <FormSearch :locations="locations"></FormSearch>
        </div>
        <footer>
            <img class="logo" src="./assets/images/logo.svg" alt="Smartfit logo">
            <p>Todos os direitos reservados - 2020</p>
        </footer>
    </div>
</template>

<script>
import FormSearch from './components/FormSearch.vue'
import axios from 'axios';

export default {
    name: 'App',
    components: {
        FormSearch,
    },
    data () {
      return {
        locations: [],
      }
    },
    created: function() {
        axios.get("http://test-frontend-developer.s3.amazonaws.com/data/locations.json").then(response => {
            this.locations = response.data.locations;
        });
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
    line-height: 49.6px;
    line-height: 3.1rem;
    font-family: 'Gotham Bold', sans-serif;
}
p {
    font-size: 15.8px;
    font-size: 0.99rem;
    line-height: 27px;
    line-height: 1.68rem;
    letter-spacing: 0;
    font-family: 'Gotham', sans-serif;
}
header {
    width: 100%;
    text-align: center;
    padding: 26px 0;
    background-color: #000;
}
header .logo {
    width: 185px;
}
.container {
    max-width: 920px;
    padding: 80px 10px;
    margin: 0 auto;
}
.header .headline {
    width: 100px;
    height: 10px;
    border: none;
    margin: 20px auto 35px 0;
    background-color: #333;
}
footer {
    color: #fff;
    width: 100%;
    text-align: center;
    background-color: #333333;
    padding: 50px 0 80px;
}
footer .logo {
    width: 100px;
    margin-bottom: 20px;
}
@media screen and (max-width: 768px) {
    .container {
        padding: 100px 26px;
    }
}
@media screen and (max-width: 576px) {
    header {
        padding: 35px 0;
    }
    header .logo {
        width: 245px;
    }
    h1 {
        font-size: 46px;
        font-size: 2.87rem;
        line-height: 56px;
        line-height: 3.5rem;
    }
    p {
        font-size: 17.6px;
        font-size: 1.13rem;
        line-height: 28px;
        line-height: 1.75rem;
    }
    .header .headline {
        width: 130px;
        height: 13px;
        margin: 30px auto 50px 0;
    }
    footer .logo {
        width: 120px;
    }
    footer p {
        font-size: 1.3rem;
        padding: 0 30px;
    }

}
</style>
