<template>
    <section class="container">
        <article :class="{background:true,sunset:(hour>=19 && hour<=21), sunrise:(hour>=5 && hour<=7), night:hour>=22 || hour<=4,day:(hour>=8 && hour<=18) }">
            <aside>
                <h3>{{weatherData.location?.name}} - {{weatherData.location?.region}} - {{weatherData.location?.country}} </h3>
                <h2>{{weatherData.current?.temp_c}}°</h2>
                <h5>{{weatherData.current?.condition.text}}</h5>
                <img :src="weatherData.current?.condition.icon" alt="">
                <h6><i class="fa-solid fa-temperature-quarter"></i> UV Index: {{weatherData.current?.uv}}</h6>
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
            hour:"",
            show:true
        }
        
    },
    methods:{
        
        async getData(){
            try{
                 console.log(this.show);

                 await fetch(this.api).then(res=>res.json()).then(data=>this.weatherData=data);
                //  console.log(this.weatherData)
                 this.dateFormat = new Date(this.weatherData.location?.localtime_epoch*1000).toLocaleString('en-US',{ weekday: 'long', year: 'numeric', month: 'long', day: 'numeric' })
                 this.hour=new Date(this.weatherData.location?.localtime_epoch*1000).getHours();
                //  console.log(`${(this.hour).getHours()}`)
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
    background-position: top;
    padding: 3vh;
    color: white;
    background-size: cover;
    background-repeat: no-repeat;
    /* background-image: url("https://cdn.vox-cdn.com/thumbor/R4HOj89cekaEOkDW2hOiz8QnjK4=/0x0:2560x1440/1400x1050/filters:focal(1280x720:1281x721)/cdn.vox-cdn.com/uploads/chorus_asset/file/21857937/Land_Sea_UpcomingProject_TeaserImage.png"); */
    /* background-image: linear-gradient(to bottom,#FFC26F,#C38154,#884A39); */
    height: fit-content;
    width: 90%;
    border-radius: 15px;
    display: flex;
    justify-content: space-between;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

.sunset {
    background-image: url("https://149362454.v2.pressablecdn.com/previously/wp-content/uploads/sites/5/2015/02/b04_QuarterPipe.png");
}

.sunrise {
    background-image: url("https://cdn.vox-cdn.com/thumbor/R4HOj89cekaEOkDW2hOiz8QnjK4=/0x0:2560x1440/1400x1050/filters:focal(1280x720:1281x721)/cdn.vox-cdn.com/uploads/chorus_asset/file/21857937/Land_Sea_UpcomingProject_TeaserImage.png");

}
.night {
    background-image: url("https://i.pinimg.com/originals/a2/48/92/a24892f0b14a4a847a63139741de6fbf.jpg");
}
.day {
    background-image: url("https://i.pinimg.com/originals/f1/3d/a2/f13da27bb30ffbd69cb504d52767e1b9.jpg");
}

aside {
    display: flex;
    flex-direction: column;

}

aside img {
    width: 12vh;
    height: 12vh;
}
h3,h5 {
    color: white;
    font-size: 30px;
    font-weight: 400;
}
h2 {
    color: white;
    font-size: 135px;

}
h6 {
    font-size: 20px;

}
p {
    font-size: 25px;

}
</style>