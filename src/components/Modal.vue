<template>
  <div id="myModal" class="modal">
  <div class="modal-content">
    <aside>
        <span @click="passModal" class="close">&times;</span>
    </aside>  
    <article >
      <h2>{{dayData.date}}</h2>
    </article>
    <h1 style="font-size: 10vh;">{{dayData.day.avgtemp_c}}ºC</h1>
    <section class="box2">
      <div class="time" v-for="hour,index in dayData.hour" :key="index" >
        <p>{{formatHour(hour.time)}}</p>
        <img :src=hour.condition.icon alt="">
        <p>{{hour.condition.text}}</p>
        <p>{{hour.temp_c}} ºC</p>
      </div>
    </section>
    <section class="big_box">
      <div class="box">
        <h2>Air Humidity</h2>
        <p class="number">{{dayData.day.avghumidity}}%</p>
      </div>
      <div class="box">
        <aside>
          <h2>Condition</h2>
          <img :src=dayData.day.condition.icon alt="">
          <p>{{dayData.day.condition.text}}</p>
        </aside>
      </div>
      <div class="box">
        <h2>Max Temp</h2>
        <p class="number">{{dayData.day.maxtemp_c}}ºC</p>
      </div>
      <div class="box">
        <h2>Min Tempe</h2>
        <p class="number">{{dayData.day.mintemp_c}}ºC</p>
      </div>
      <div class="box">
        <h2>Air Speed</h2>
        <p class="number">{{dayData.day.avgvis_km}}Km/h</p>
      </div>
      <div class="box">
        <h2>UV Rays</h2>
        <p class="number">{{dayData.day.uv}}</p>
      </div>
    </section>

                                
  </div>
  </div>
</template>

<script>
import moment from 'moment';
export default {
  data() {
    return {
      currentIndex: 0,
      arrayIndex: [],
    };
  },
  props:{
    dayData:Object
  },
  methods:{
    passModal() {
      this.$emit('closeModal',false);
    },
    formatHour(time) {
    return moment(time).format("HH:mm");
  }
  },
    mounted() {
    console.log(this.currentIndex);
  },
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
  background-color: #0b99e5;
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
  background-color: #4FAFE9;
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
  align-items: center;
  margin-bottom: 20px;
  width: 100%;
  overflow-x: scroll;
  white-space: nowrap;
  column-gap: 2vh;
}
.time{
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 1000px;
  padding: 2%;
  margin-right: 10px;
  background-color: #4FAFE9;
}
.time img{
  width: 90px;
}
h1{
  padding-bottom: 4vh;
}
</style>