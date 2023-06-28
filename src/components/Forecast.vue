<template>
<section class="container">
     <Transition name="fade" appear>
    <Modal v-if="modal" @closeModal="closeModalfromChild($event)" :dayData="modalData"/>
      </Transition>
    <h2>10 Day Forecast</h2>
    <section class="tab">
    <article @click="showModal(index)" v-for="(data,index) in forecastData" :key="index">
        <p class="header"><span>{{new Date(data.date_epoch*1000).toLocaleString('en-US',{ weekday: 'long'})}}</span><span>{{new Date(data.date_epoch*1000).toLocaleString('en-US',{ day: 'numeric', month:'long'})}}</span></p>
        <section class="inner-tab">
        <aside>
            <h5 v-if="temp=='' || temp=='C'">{{data.day.avgtemp_c}}°C</h5>
            <h5 v-else>{{data.day.avgtemp_f}}°F</h5>
        </aside>
        <aside>
            <i class="fa-solid fa-sun sunrise"></i>
            <p>Sunrise</p>
            <p style="">{{data.astro.sunrise}}</p>
        </aside>
        <aside>
            <i class="fa-solid fa-sun sunset"></i>
            <p>Sunset</p>
            <p>{{data.astro.sunset}}</p>
        </aside>
        <aside>
        <img :src="data.day.condition.icon" alt="">
        <p>{{data.day.condition.text}}</p>
        </aside>

        </section>
    </article>
    </section>

</section>
</template>

<script>
import Modal from './Modal.vue';
export default {
    name:'Forecast',
    props:{
        city:String,
        temp:String
    },
    components:{
        Modal
    },
    data() {

        return {
            // api: "/src/services/forecastResponse.json",
            api:`http://api.weatherapi.com/v1/forecast.json?key=3fba2596a97d4f74b1014949231406&q=${this.city}&days=10&aqi=no&alerts=no`,
            forecastData:{},
            week:'',
            modal:false, 
            modalData:{}
        }
        
    },  watch:{
        city(newV,oldV) {
            this.getForecast(newV)
        }
    },
    methods:{
        
        async getForecast(cities="Vancouver"){
            try{

                 await fetch(`http://api.weatherapi.com/v1/forecast.json?key=3fba2596a97d4f74b1014949231406&q=${cities}&days=10&aqi=no&alerts=no`).then(res=>res.json()).then(data=>this.forecastData=data.forecast.forecastday);
                console.log(this.forecastData);
                 this.week = new Date(this.forecastData[0].date_epoch*1000).toLocaleString('en-US',{ weekday: 'long'})
                    // console.log(this.week)
            } catch(e) {
                console.log(e);
            }
        },

        showModal(i){
            console.log(i)
            this.modal=true;
            this.modalData=this.forecastData[i];
        },
        closeModalfromChild(modalState){
            this.modal=modalState
            // console.log(modalState)
        }

    },
    created(){
        this.getForecast();
    }
}
</script>
<style scoped>
.container {
/* padding: 7vh;*/
display: flex;
flex-direction: column;
justify-content: start;
row-gap: 1vh;
width: 80%; 

}
.tab {
    display: flex; 
    flex-direction: column;
    row-gap: 1vh;
    width: 60%; 

}
article{
    width: 80%;
    display: flex;
    cursor: pointer;
    flex-direction: column;
    justify-content: space-between;
    background-color: #50afe9;
    color: white;
    border-radius: 4px;
    height: fit-content;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 1px 4px;

}
aside {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    width: 30%;
}
.header {
        background-color: #0b99e5;
        display: flex;
        justify-content: space-between;
        padding: 1vh;
}
.inner-tab{
    display: flex;
    padding: 1vh;
    justify-content: space-between;
}
h5 {
    font-size: 60px;
}

.sunset {
    color: rgb(246, 175, 43);
}

.sunrise {
    color: yellow;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.4s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>