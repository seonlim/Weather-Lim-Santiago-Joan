<template>
  <section class="informations">
    <h3>Additional Information</h3>
    <div class="info">
        <section>
            <img src="/src/assets/img/wind.png" alt="wind">
            <small>Wind</small>
        </section>
        <span> 10km/h</span>
    </div>
    <div class="info">
        <section>
            <img src="/src/assets/img/temperature.png" alt="temperature">
            <small>Feels Like </small>
        </section>
        <span>20°C</span>
        <p>Similar to the actual temperature.</p>
    </div>
    <div class="info">
        <section>
            <img src="/src/assets/img/humidity.png" alt="humidity">
            <small>Humidity</small>
        </section>
        <span> 64%</span>
    </div>
    <div class="info">
        <section>
            <img src="/src/assets/img/uv.png" alt="uv">
            <small>UV Index</small>
        </section>
        <span>7</span>
        <span>High</span>
    </div>
  </section>
</template>

<script>
export default {
    name:'Informations',
    props:{
        informationData: {}
    }
}
</script>

<style scoped>
.informations {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 2vh;
  color: white;
  font-size: 20px;
}

.informations h3 {
    color: black;
}

.info {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
  justify-content: space-evenly;
  /* align-items: center; */
  padding: 3vh;
  border-radius: 20px;
  background-color: #50afe9;
  width: 25vh;
  height: 25vh;
}

.info > section {
    display: flex;
    align-items: center;
    column-gap: 2vh;
}

.info small {
    font-size: 18px;
}

.info span {
    font-weight: 600;
    font-size: 28px;
}

.info p {
    font-size: 16px;
}

.info img {
    width: 4vh;
    height: 4vh;
}


</style>

