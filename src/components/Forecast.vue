<template>
<section class="container">
    <h2>10 Day Forecast</h2>
    <section class="tab">
    <article v-for="(data,index) in forecastData" :key="index">
        <p class="header"><span>{{new Date(data.date_epoch*1000).toLocaleString('en-US',{ weekday: 'long'})}}</span><span>{{new Date(data.date_epoch*1000).toLocaleString('en-US',{ day: 'numeric', month:'long'})}}</span></p>
        <section class="inner-tab">
        <aside>
        <h5>{{data.day.avgtemp_c}}°</h5>         
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

export default {
    name:'Forecast',
    components:{
  
    },
    data() {

        return {
            api: "/src/services/forecastResponse.json",
            forecastData:{},
            week:''
        }
        
    },
    methods:{
        
        async getForecast(){
            try{

                 await fetch(this.api).then(res=>res.json()).then(data=>this.forecastData=data.forecast.forecastday);
                console.log(this.forecastData[0]);
                 this.week = new Date(this.forecastData[0].date_epoch*1000).toLocaleString('en-US',{ weekday: 'long'})
                    console.log(this.week)
            } catch(e) {
                console.log(e);
            }
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
    width: 70%;
    display: flex;
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


</style>