<template>
    <div>
        <div id="form">
            <div class="title">
                <img src="../assets/images/icon-hour.png" alt="Ícone de relógio"><span>Horário</span>
                <h2>Qual período quer treinar?</h2>
            </div>
            <div class="radiobuttons">
                <div class="radiobutton">
                    <input type="radio" id="manha" value="06:00 às 12:00" v-model="scheduleTime"><div class="check"></div>
                    <label for="manha">Manhã</label>
                    <span>06:00 às 12:00</span>
                </div>
                <div class="radiobutton">
                    <input type="radio" id="tarde" value="12:01 às 18:00" v-model="scheduleTime"><div class="check"></div>
                    <label for="tarde">Tarde</label>
                    <span>12:01 às 18:00</span>
                </div>
                <div class="radiobutton">
                    <input type="radio" id="noite" value="18:01 às 23:00" v-model="scheduleTime"><div class="check"></div>
                    <label for="noite">Noite</label>
                    <span>18:01 às 23:00</span>
                </div>
            </div>
            <div class="results">
                <input type="checkbox" id="showclosed" class="checkbox" v-model="showClosed">
                <label for="showclosed">Exibir unidades fechadas</label>
                <p>Resultados encontrados: <strong>{{ filteredLocations.length }}</strong></p>
            </div>
            <div class="buttons">
                <a class="btn primary" @click="resultSearch()">Encontrar unidade</a>
                <a class="btn outline" @click="cleanSearch()">Limpar</a>
            </div>
        </div>
        <Legend></Legend>
        <div class="units">
            <Location v-for="(location, index) in filteredLocations" :key="index" :test="index" :location="location"></Location>
        </div>
        <div><p></p></div>
    </div>
</template>

<script>
import Legend from '../components/Legend.vue'
import Location from '../components/Location.vue'

export default {
    name: 'FormSearch',
    components: {
        Legend,
        Location,
    },
    props: {
        locations: '',
    },
    data () {
      return {
        scheduleTime: '',
        showClosed: false,
        filteredLocations: [],
      }
    },
    computed: {
        splitSchedule: function() {
            let split = this.scheduleTime.split(" às ");
            split.forEach((hour, index) => {
                split[index] = hour.replace(':','');
            });
            return split;
        }
    },
    methods: {
        splitHour: function(scheduleHour) {
            let split = scheduleHour.split(" às ");
            split.forEach((hour, index) => {
                split[index] = hour.replace('h','') ;
                split[index] += (hour.length > 3 ) ? "" : "00";
            });
            return split;
        },
        checkTime: function(schedules, location) {
            let scheduleHour;
            if (schedules) {
                for (var i = 0; i < schedules.length; i++) {
                    if (schedules[i].hour != "Fechada") {
                        scheduleHour = this.splitHour(schedules[i].hour);
                        if (scheduleHour[0] >= this.splitSchedule[0] && scheduleHour[0] < this.splitSchedule[1] ||
                            scheduleHour[1] >  this.splitSchedule[0] && scheduleHour[1] <= this.splitSchedule[1] ||
                            scheduleHour[0] <= this.splitSchedule[0] && scheduleHour[1] >= this.splitSchedule[1])
                        {
                            return true;
                        }
                    }
                };
            }
            return false;
        },
        resultSearch: function() {
            if (!this.scheduleTime) {
                this.filteredLocations = this.showClosed ? 
                        this.locations.filter(location => location.opened == true || location.opened == false)
                      : this.locations.filter(location => location.opened == true);
            } else {
                this.filteredLocations = this.showClosed ?
                        this.locations.filter(location => this.checkTime(location.schedules, location) == true || location.opened == false)
                      : this.locations.filter(location => this.checkTime(location.schedules, location) == true && location.opened == true);
            }
        },
        cleanSearch: function() {
            this.filteredLocations = [];
            this.showClosed = false;
            this.scheduleTime = '';
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#form {
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
    flex-wrap: wrap;
    justify-content: center;
    margin: 0 -20px;
}
@media screen and (max-width: 576px) {
    #form {
        font-size: 20px;
        font-size: 1.25rem;
        padding: 25px;
    }
    .title img {
        width: 39px;
        margin-right: 13px;
    }
    .title span {
        font-size: 17.6px;
        font-size: 1.15rem;
    }
    .title h2 {
        font-size: 23.5px;
        font-size: 1.98rem;
    }
    .results {
        font-size: 21.6px;
        font-size: 1.35rem;
        flex-wrap: wrap;
        justify-content: center;
        padding: 10px 0;
        margin: 30px 0;
    }
    .results p {
        font-size: 21.6px;
        font-size: 1.35rem;
    }
    .results strong {
        font-size: 25.6px;
        font-size: 1.6rem;
    }
    .checkbox + label {
        margin-bottom: 20px;
    }
    .buttons {
        flex-direction: column;
    }
    .btn {
        font-size: 19.2px;
        font-size: 1.2rem;
        padding: 20px 40px;
        margin: 10px 0;
        max-width: 100%;
    }

}
</style>
