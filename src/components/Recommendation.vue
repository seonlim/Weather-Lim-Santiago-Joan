<template>
  <section class="recommendations">
    <h3>Weather Clothing Guide</h3>
    <section v-if="infoWeather.current?.temp_c >= 27">
      <article>
        <h3>Accessories</h3>
        <figure>
          <div><img src="../assets/img/cap.png" alt="cap" /></div>
          <div><img src="../assets/img/sunglasses.png" alt="sunglasses" /></div>
          <div><img src="../assets/img/sunhat.png" alt="sunhat" /></div>
        </figure>
      </article>
      <article>
        <h3>Top</h3>
        <figure>
          <div><img src="../assets/img/tshirt.png" alt="tshirt" /></div>
          <div><img src="../assets/img/polo-shirt.png" alt="polo" /></div>
          <div>
            <img src="../assets/img/hawaiian-shirt.png" alt="half-shirt" />
          </div>
        </figure>
      </article>
      <article>
        <h3>Bottoms</h3>
        <figure>
          <div><img src="../assets/img/shorts(1).png" alt="shorts1" /></div>
          <div><img src="../assets/img/shorts(3).png" alt="shorts3" /></div>
          <div><img src="../assets/img/shorts(2).png" alt="shorts2" /></div>
        </figure>
      </article>
      <article>
        <h3>Shoes</h3>
        <figure>
          <div><img src="../assets/img/sandals.png" alt="shorts3" /></div>
          <div><img src="../assets/img/sandals (2).png" alt="shorts2" /></div>
          <div><img src="../assets/img/flip-flops.png" alt="shorts1" /></div>
        </figure>
      </article>
    </section>
    <section v-else-if="infoWeather.current?.temp_c >= 23 && infoWeather.current?.temp_c < 27">
  <h2>more than 23 , less than 27</h2>
</section>
<section v-else-if="infoWeather.current?.temp_c >= 20 && infoWeather.current?.temp_c < 23">
  <h2>more than 20 , less than 23</h2>
</section>
<section v-else-if="infoWeather.current?.temp_c >= 16 && infoWeather.current?.temp_c < 20">
  <h2>more than 16 , less than 20</h2>
</section>
<section v-else-if="infoWeather.current?.temp_c >= 12 && infoWeather.current?.temp_c < 16">
  <h2>more than 12 , less than 16</h2>
</section>
<section v-else-if="infoWeather.current?.temp_c >= 9 && infoWeather.current?.temp_c < 12">
  <h2>more than 9 , less than 12</h2>
</section>
<section v-else-if="infoWeather.current?.temp_c >= 5 && infoWeather.current?.temp_c < 9">
  <h2>more than 5 , less than 9</h2>
</section>
<section v-else-if="infoWeather.current?.temp_c < 5">
  <h2>less than 5</h2>
</section>
  </section>
</template>

<script>
export default {
  name: "Recommendation",
  props: {
    infoWeather: Object,
  },
};
</script>

<style>
.recommendations {
  display: flex;
  flex-direction: column;
  row-gap: 2vh;
}

.recommendations h3 {
  font-size: 24px;
}

.recommendations > section {
  display: flex;
  flex-direction: column;
  background-color: #0b99e5;
  border-radius: 20px;
  padding: 5%;
  row-gap: 3vh;
  color: whitesmoke;
}

.recommendations article {
  display: flex;
  flex-direction: column;
  row-gap: 3vh;
}

.recommendations > section figure {
  display: flex;
  justify-content: space-around;
}

.recommendations > section img {
  width: 100%;
}

.recommendations div {
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 20px;
  width: 20%;
  padding: 3%;
}
</style>