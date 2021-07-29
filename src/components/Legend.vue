<template>
    <div class="legends">
        <div class="items">
            <p class="title"><strong>Máscara</strong></p>
            <div class="item">
                <img src="../assets/images/required-mask.png" alt="Símbolo de uso orbigatório de máscara">
                <p>Obrigatório</p>
            </div>
            <div class="item">
                <img src="../assets/images/recommended-mask.png" alt="Símbolo de uso recomendado de máscara">
                <p>Recomendado</p>
            </div>
        </div>
        <div class="items">
            <p class="title"><strong>Toalha</strong></p>
            <div class="item">
                <img src="../assets/images/required-towel.png" alt="Símbolo de uso orbigatório de toalha própria">
                <p>Obrigatório</p>
            </div>
            <div class="item">
                <img src="../assets/images/recommended-towel.png" alt="Símbolo de uso recomendado de toalha própria">
                <p>Recomendado</p>
            </div>
        </div>
        <div class="items">
            <p class="title"><strong>Bebedouro</strong></p>
            <div class="item">
                <img src="../assets/images/partial-fountain.png" alt="Símbolo de uso de bebedouro parcialmente liberado">
                <p>Parcial</p>
            </div>
            <div class="item">
                <img src="../assets/images/forbidden-fountain.png" alt="Símbolo de proibído uso de bebedouro">
                <p>Probido</p>
            </div>
        </div>
        <div class="items">
            <p class="title"><strong>Vestiários</strong></p>
            <div class="item">
                <img src="../assets/images/required-lockerroom.png" alt="Símbolo de uso liberado de vestiários">
                <p>Liberado</p>
            </div>
            <div class="item">
                <img src="../assets/images/partial-lockerroom.png" alt="Símbolo de uso parcialmente liberado de vestiários">
                <p>Parcial</p>
            </div>
            <div class="item">
                <img src="../assets/images/forbidden-lockerroom.png" alt="Símbolo de uso proibído de vestiários">
                <p>Fechado</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Legend',
    props: {
    
    }
} 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.legends {
    color: #000;
    display: flex;
    flex-direction: row;
    justify-content: center;
    background-color: #F5F5F5;
    margin-bottom: 40px;
}
.items {
    display: flex;
    flex-wrap: wrap;
    text-align: center;
    justify-content: center;
    align-items: center;
    padding: 25px 0 10px;
}
.items .item {
    margin: 10px 5px;
}
.legends .items .title {
    text-align: center;
    font-family: 'Gotham Black';
    flex-basis: 100%;
}
.items .item img {
    width: 60px;
}
@media screen and (max-width: 768px) {
    .legends {
        flex-wrap: wrap;
    }
    .items {
        width: 50%;
    }
}
@media screen and (max-width: 576px) {
    .legends {
        padding: 50px 20px;
    }
    .items {
        width: 100%;
        justify-content: space-around;
    }
    .items .item img {
        width: 80px;
    }
}
</style>
