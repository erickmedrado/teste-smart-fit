<template>
    <div>
        <div id="form">
            <div class="title">
                <img src="../assets/images/icon-hour.png" alt="Ícone de relógio"><span>Horário</span>
                <h2>Qual período quer treinar?</h2>
            </div>
            <div class="radiobuttons">
                <div class="radiobutton">
                    <input type="radio" id="manha" value="Manha" v-model="scheduleTime"><div class="check"></div>
                    <label for="manha">Manhã</label>
                    <span>06:00 às 12:00</span>
                </div>
                <div class="radiobutton">
                    <input type="radio" id="tarde" value="Tarde" v-model="scheduleTime"><div class="check"></div>
                    <label for="tarde">Tarde</label>
                    <span>12:01 às 18:00</span>
                </div>
                <div class="radiobutton">
                    <input type="radio" id="noite" value="Noite" v-model="scheduleTime"><div class="check"></div>
                    <label for="noite">Noite</label>
                    <span>18:01 às 23:00</span>
                </div>
            </div>
            <div class="results">
                <input type="checkbox" id="showclosed" class="checkbox" v-model="showClosed">
                <label for="showclosed">Exibir unidades fechadas</label>
                <p>Resultados encontrados: <strong>0</strong></p>
            </div>
            <div class="buttons">
                <button class="btn primary">Encontrar unidade</button>
                <button class="btn outline">Limpar</button>
            </div>
        </div>
        <Legend></Legend>
        <div class="units">
            <Unit></Unit>
            <Unit></Unit>
            <Unit></Unit>
        </div>
    </div>
</template>

<script>
import Legend from '../components/Legend.vue'
import Unit from '../components/Unit.vue'

export default {
    name: 'FormSearch',
    components: {
        Legend,
        Unit,
    },
    props: {
    
    },
    data () {
      return {
        scheduleTime: '',
        showClosed: '',
      }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#form {
    /* width: 100%; */
    color: #808080;
    font-family: 'Gotham Ligth';
    border: 4px solid #ededed;
    border-radius: 8px;
    padding: 18px;
    margin: 42px 0;
}
.title {
    width: 100%;
    margin-bottom: 10px;
    border-bottom: 2px solid #ededed;
}
.title span {
    font-size: 14px;
    font-size: 0.87rem;
    font-family: 'Gotham';
}
.title img {
    width: 28.5px;
    margin-right: 10px;
    vertical-align: middle;
}
.title h2 {
    font-size: 23.5px;
    font-size: 1.46rem;
    margin: 32px 10px 12px;
}
.radiobuttons .radiobutton {
    border-bottom: 2px solid #ededed;
}
.results {
    color: #333;
    font-family: 'Gotham';
    display: flex;
    justify-content: space-between;
    padding: 0 2px;
    margin: 50px 0 30px;
    vertical-align: middle;
}
.results strong {
    font-size: 22px;
    font-size: 1.37rem;
    font-family: 'Gotham Bold';
    vertical-align: middle;
    margin-top: 2px;
}
.buttons {
    display: flex;
    justify-content: center;
}
.btn {
    width: 100%;
    max-width: 318px;
    border: none;
    color: #000;
    font-size: 16px;
    font-size: 1rem;
    text-align: center;
    font-family: 'Gotham Bold';
    border-radius: 5px;
    text-decoration: none;
    text-transform: uppercase;
    padding: 13px 15px;
    margin: 0 10px;
}
.btn.primary {
    background-color: #ffb612;
}
.btn.outline {
    background-color: #fff;
    border: 2px solid #ccc;
}
.units {
    display: flex;
    gap: 20px;
    margin: 0 -10px;
}
</style>
