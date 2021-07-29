<template>
    <div class="box">
        <div class="header">
            <h1 class="open">Aberto</h1>
            <h2>Vicente Linhares</h2>
            <p>Rua Tibúrcio Cavalcante, 1885 - Meireles<br>Fortaleza, CE</p>
        </div>
        <div class="legends">
            <img src="../assets/images/required-mask.png" alt="">
            <img src="../assets/images/required-towel.png" alt="">
            <img src="../assets/images/partial-fountain.png" alt="">
            <img src="../assets/images/forbidden-lockerroom.png" alt="">
        </div>
        <div class="days">
            <div class="day">
                <h3>Seg. à Sex.</h3>
                <p>06h às 22h</p>
            </div>
            <div class="day">
                <h3>Sáb.</h3>
                <p>09h às 18h</p>
            </div>
            <div class="day">
                <h3>Dom.</h3>
                <p>Fechada</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Location',
    props: {
    
    }
} 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
    width: 30%;
    border-radius: 5px;
    background-color: #F5F5F5;
    -webkit-box-shadow: 0px 0px 10px -1px #ccc; 
    box-shadow: 0px 0px 10px -1px #ccc;
    padding: 15px;
}
.box .header {
    padding-bottom: 12px ;
    border-bottom: 2px solid #ccc;
}
.box .header p {
    color: #808080;
    font-size: 14px;
    line-height: 16px;
}
.box h1 {
    font-size: 14px;
    font-size: 0.87rem;
    line-height: 18px;
    line-height: 1.12rem;
}
.box h2 {
    font-size: 25.5px;
    font-family: 'Gotham Bold';
    margin: 14px 0 16px;
}
.box h3 {
    font-size: 22px;
    line-height: 28px;
    font-family: 'Gotham Bold';
}
.box .legends {
    display: flex;
    padding: 20px 0 28px;
}
.box .legends img {
    width: 25%;
}
.box .days {
    display: flex;
    flex-wrap: wrap;
}
.box .days .day {
    width: 50%;
    margin-bottom: 25px;
}
.box .days .day h3 {
    margin-bottom: 4px;
}
.open {
    color: #2fc022;
}
.closed {
    color: #dc0a17
}
</style>
