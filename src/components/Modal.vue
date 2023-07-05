<template>
  <div id="myModal" class="modal">
  <div class="modal-content" :class="{sunsetS:(hour>=19 && hour<=20), sunriseS:(hour>=5 && hour<=7), nightS:hour>=21 || hour<=4,dayS:(hour>=8 && hour<=18) }">
    <aside>
        <span @click="passModal" class="close">&times;</span>
    </aside>  
    <article>
      <h2>{{dayData.date}}</h2>
    </article>
    <h1 style="font-size: 10vh;">{{dayData.day.avgtemp_c}}ºC</h1>
    <section class="box2">
      <a class="prev" @click="prevSlide">&#10094;</a>
      <div class="time" v-for="hour,index in dayData.hour" :key="index" v-show="index === currentIndex">
        <p>{{hour.time}}</p>
        <img :src=hour.condition.icon alt="">
        <p>{{hour.condition.text}}</p>
        <p>{{hour.temp_c}} ºC</p>
      </div>
      <a class="next" @click="nextSlide">&#10095;</a>
    </section>
    <section class="big_box">
      <div class="box" :class="{sunset:(hour>=19 && hour<=20), sunrise:(hour>=5 && hour<=7), night:hour>=21 || hour<=4,day:(hour>=8 && hour<=18) }">
        <h2>Air Humidity</h2>
        <p class="number">{{dayData.day.avghumidity}}%</p>
      </div>
      <div class="box" :class="{sunset:(hour>=19 && hour<=20), sunrise:(hour>=5 && hour<=7), night:hour>=21 || hour<=4,day:(hour>=8 && hour<=18) }">
        <aside>
          <h2>Condition</h2>
          <img :src=dayData.day.condition.icon alt="">
          <p>{{dayData.day.condition.text}}</p>
        </aside>
      </div>
      <div class="box" :class="{sunset:(hour>=19 && hour<=20), sunrise:(hour>=5 && hour<=7), night:hour>=21 || hour<=4,day:(hour>=8 && hour<=18) }">
        <h2>Max Temp</h2>
        <p class="number">{{dayData.day.maxtemp_c}}ºC</p>
      </div>
      <div class="box" :class="{sunset:(hour>=19 && hour<=20), sunrise:(hour>=5 && hour<=7), night:hour>=21 || hour<=4,day:(hour>=8 && hour<=18) }">
        <h2>Min Tempe</h2>
        <p class="number">{{dayData.day.mintemp_c}}ºC</p>
      </div>
      <div class="box" :class="{sunset:(hour>=19 && hour<=20), sunrise:(hour>=5 && hour<=7), night:hour>=21 || hour<=4,day:(hour>=8 && hour<=18) }">
        <h2>Air Speed</h2>
        <p class="number">{{dayData.day.avgvis_km}}Km/h</p>
      </div>
      <div class="box" :class="{sunset:(hour>=19 && hour<=20), sunrise:(hour>=5 && hour<=7), night:hour>=21 || hour<=4,day:(hour>=8 && hour<=18) }">
        <h2>UV Rays</h2>
        <p class="number">{{dayData.day.uv}}</p>
      </div>
    </section>

                                
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      arrayIndex: [],
    };
  },
  props:{
    dayData:Object,
    hour:Number
  },
  methods:{
    passModal() {
      this.$emit('closeModal',false);
    },
    nextSlide() {
      this.currentIndex++;
      if (this.currentIndex >= this.dayData.hour.length) {
        this.currentIndex = 0;
      }
    },
    prevSlide() {
      this.currentIndex--;
      if (this.currentIndex < 0) {
        this.currentIndex = this.dayData.hour.length - 1;
      }
    }
  },
    mounted() {
    console.log(this.currentIndex);
  }
}
</script>
<style scoped>
.modal {
  display: block;
  /* Hidden by default */
  position: fixed;
  /* Stay in place */
  z-index: 1;
  /* Sit on top */
  left: 0;
  top: 0;
  width: 100%;
  /* Full width */
  height: 100%;
  /* Full height */
  overflow: auto;
  /* Enable scroll if needed */
  background-color: rgb(0, 0, 0);
  /* Fallback color */
  background-color: rgba(0, 0, 0, 0.4);
  /* Black w/ opacity */
}

/* Modal Content/Box */
.modal-content {
  margin: 2% auto;
  /* 15% from the top and centered */
  padding: 25px;
  border: 1px solid #888;
  border-radius: 10px;
  width: 65%;
  /* Could be more or less, depending on screen size */
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  row-gap: 2vh;


}

.modal-content > aside {
    width: 100%;
}

/* The Close Button */
.close {
  color: whitesmoke;
  float: right;
  font-size: 28px;
  font-weight: bold;
}

.close:hover,
.close:focus {
  color: black;
  text-decoration: none;
  cursor: pointer;
}
article{
  display: flex;
  justify-content: space-between;
}
.big_box{
  display: flex;
  flex-wrap: wrap;
  row-gap: 3vh;
  column-gap: 3vh;
}
.box{
  display: flex;
  flex-direction: column;
  row-gap: 4vh;
  width: 40%;
  height: 16vh;
  padding: 4%;
  align-items: center;
}
.box>aside{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.number{
  font-size: 5vh;
}
.box2{
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}
.time{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.prev, .next {
  cursor: pointer;
  width: 40px;
  height: 40px;
  color: white;
  font-weight: bold;
  font-size: 20px;
  transition: 0.3s ease;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.prev {
  border-radius: 3px 0 0 3px;
  top: 0;
  right: 0;
}
.next {
  border-radius: 3px 0 0 3px;
  top: 0;
  left: 0;
}

.prev:hover, .next:hover {
  background-color: rgba(0,0,0,0.8);
}
h1{
  padding-bottom: 4vh;
}
.day {
  background-color: #0b99e5  
}

.dayS {
   background-color: #50afe9; 

}

.night{
background-color: #27374D;
}
.nightS{
background-color: #526D82;
}
.sunset {
  background-color: #884A39;

}

.sunrise{
background-color: #A0C49D;
}

.sunriseS{
background-color: #C4D7B2;
}

.sunsetS{
  background-color: #C38154;

}
</style>