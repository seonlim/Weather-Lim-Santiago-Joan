<template>
    <section class="container">
        <article class="background">
            <aside>
                <h3>{{weatherData.location?.name}} - {{weatherData.location?.region}} - {{weatherData.location?.country}} </h3>
                <h2>{{weatherData.current?.temp_c}}°</h2>
            </aside>
            <aside>
                <p>{{dateFormat}}</p>
            </aside>

        </article>
    </section>
</template>


<script>

export default {
    name:'CurrentData',
    data() {

        return {
            api: "/src/services/currentResponse.json",
            weatherData:{},
            dateFormat:"",
            show:false
        }
        
    },
    methods:{
        
        async getData(){
            try{
                 console.log(this.show);

                 await fetch(this.api).then(res=>res.json()).then(data=>this.weatherData=data);
                 console.log(this.weatherData)
                 this.dateFormat = new Date(this.weatherData.location?.localtime_epoch*1000).toLocaleString('en-US',{ weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })
                console.log();
            } catch(e) {
                console.log(e);
            }
        }

    },
    created(){
        this.getData();
    }
}
</script>
<style scoped>
.container {
padding: 7vh;
display: flex;
justify-content: center;
}
.background {
    background-position: center;
    padding: 3vh;
    color: white;
    background-size: cover;
    background-repeat: no-repeat;
    background-image: linear-gradient(to bottom,#FFC26F,#C38154,#884A39);
    height: 50vh;
    width: 95%;
    border-radius: 15px;
    display: flex;
    justify-content: space-between;
}
h3 {
    color: white;
    font-size: 30px;
    font-weight: 400;
}
h2 {
    color: white;
    font-size: 140px;

}
p {
    font-size: 30px;

}
</style>