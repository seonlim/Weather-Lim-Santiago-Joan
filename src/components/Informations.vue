<template>
  <section class="informations">
    <h3>Additional Information</h3>
    <article>
      <div class="row">
          <div class="info">
            <section>
              <img src="/src/assets/img/temperature.png" alt="temperature" />
              <small>Feels Like </small>
            </section>
            <span>{{ infoWeather.current?.feelslike_c }} °C</span>
            <p>{{ getTemperatureMessage }}</p>
          </div>
          <div class="info">
            <section>
              <img src="/src/assets/img/uv.png" alt="uv" />
              <small>UV Index</small>
            </section>
            <span>{{ infoWeather.current?.uv }}</span>
            <small>{{getUVIndexLevel(infoWeather.current?.uv) }}</small>
          </div>
      </div>
      <div class="row">
          <div class="info">
            <section>
              <img src="/src/assets/img/humidity.png" alt="humidity" />
              <small>Humidity</small>
            </section>
            <span>{{ infoWeather.current?.humidity }} %</span>
          </div>
          <div class="info">
            <section>
              <img src="/src/assets/img/wind.png" alt="wind" />
              <small>Wind</small>
            </section>
            <span>{{ infoWeather.current?.wind_kph }} km/h</span>
          </div>
      </div> 
    </article>
  </section>
</template>

<script>
export default {
  name: "Informations",
  props:{
    infoWeather:Object
  },
  data() {
    return {
        uvIndexLevel: "",
    };
  },
  methods: {
    getUVIndexLevel(uvIndex) {
      if (uvIndex < 3) {
        return "Low";
      } else if (uvIndex < 6) {
        return "Moderate";
      } else if (uvIndex < 8) {
        return "High";
      } else if (uvIndex < 11) {
        return "Very High";
      } else {
        return "Extreme";
      }
    },
  },
  computed: {
    getTemperatureMessage() {
      const temperatureDifference = this.infoWeather.current?.feelslike_c - this.infoWeather.current?.temp_c;
      if (temperatureDifference >= 10) {
        return "It's too cold";
      } else if (temperatureDifference >= 5) {
        return "Significantly different from the actual temperature";
      } else if (temperatureDifference >= 2) {
        return "Little bit different from the actual temperature";
      } else {
        return "Similar to the actual temperature.";
      }
    }
  }
};
</script>

<style scoped>
.informations {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
  color: white;
  font-size: 20px;
  /* width: 50%; */
}

.informations > article {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
}

.row {
    display: flex;
    column-gap: 2vh;
}

.informations h3 {
  color: black;
}

.info {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
  justify-content: space-evenly;
  padding: 3vh;
  border-radius: 20px;
  background-color: #50afe9;
  width: 34vh;
  height: 27vh;
  text-align: center;
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
  font-weight: 700;
  font-size: 45px;
}

.info p {
  font-size: 16px;
}

.info img {
  width: 4vh;
  height: 4vh;
}
</style>

