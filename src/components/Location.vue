<template>
    <div class="box">
        <div class="header">
            <h1 class="opened" v-if="location.opened">Aberto</h1>
            <h1 class="closed" v-else>Fechado</h1>
            <h2 v-html="location.title"></h2>
            <p v-html="location.content"></p>
        </div>
        <div class="legends" v-if="location.opened">
            <img v-if="location.mask"    :src="require('@/assets/images/'+location.mask+'-mask.png')" :alt="location.mask+' mask'">
            <img v-if="location.towel"   :src="require('@/assets/images/'+location.towel+'-towel.png')" :alt="location.towel+' towel'">
            <img v-if="fountainStatus"   :src="require('@/assets/images/'+fountainStatus+'-fountain.png')" :alt="fountainStatus+' fountain'">
            <img v-if="lockerroomStatus" :src="require('@/assets/images/'+lockerroomStatus+'-lockerroom.png')" :alt="lockerroomStatus+' locker room'">
        </div>
        <div class="days" v-if="location.opened">
            <div class="day" v-for="(day, index) in location.schedules" :key="index">
                <h3>{{ day.weekdays }}</h3>
                <p>{{ day.hour }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Location',
    props: {
        location: '',
        test: ''
    },
    computed: {
        fountainStatus: function() {
            if (this.location.fountain == "not_allowed")
                return "forbidden";
            else {
                return this.location.fountain;
            }
        },
        lockerroomStatus: function() {
            if (this.location.locker_room == "allowed")
                return "required";
            else if (this.location.locker_room == "not_allowed")
                return "partial";
            else if (this.location.locker_room == "closed")
                return "forbidden";
        }
    }
} 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.box {
    width: 28%;
    border-radius: 5px;
    background-color: #F5F5F5;
    -webkit-box-shadow: 0px 0px 10px -1px #ccc; 
    box-shadow: 0px 0px 10px -1px #ccc;
    padding: 15px;
    margin: 10px;
}
.box .header {
    padding-bottom: 12px ;
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
    border-top: 2px solid #ccc;
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
.opened {
    color: #2fc022;
}
.closed {
    color: #dc0a17
}
@media screen and (max-width: 768px) {
    .box {
        width: 43%;
    }
}
@media screen and (max-width: 576px) {
    .box {
        width: 100%;
    }
}
</style>
