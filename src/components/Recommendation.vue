<template>
  <section class="recommendations">
    <h3>Weather Clothing Guide</h3>
    <!--more than 23-->
    <section v-if="infoWeather.current?.temp_c >= 23">
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
    <!-- 19 ~ 23-->
    <section
      v-else-if="
        infoWeather.current?.temp_c >= 19 && infoWeather.current?.temp_c < 23
      "
    >
      <article>
        <h3>Accessories</h3>
        <figure>
          <div><img src="../assets/img/cap (1).png" alt="accesories1" /></div>
          <div>
            <img src="../assets/img/sunglasses.png" alt="accesories2" />
          </div>
          <div><img src="../assets/img/sunhat(1).png" alt="accesories3" /></div>
        </figure>
      </article>
      <article>
        <h3>Top</h3>
        <figure>
          <div><img src="../assets/img/sleeves.png" alt="top1" /></div>
          <div><img src="../assets/img/shirt (1).png" alt="top2" /></div>
          <div>
            <img src="../assets/img/shirt (2).png" alt="top3t" />
          </div>
        </figure>
      </article>
      <article>
        <h3>Bottoms</h3>
        <figure>
          <div><img src="../assets/img/pants (3).png" alt="bottoms1" /></div>
          <div><img src="../assets/img/loose-pants.png" alt="bottoms2" /></div>
          <div><img src="../assets/img/pants (4).png" alt="bottoms3" /></div>
        </figure>
      </article>
      <article>
        <h3>Shoes</h3>
        <figure>
          <div><img src="../assets/img/sneakers.png" alt="shoes1" /></div>
          <div><img src="../assets/img/sneakers (1).png" alt="shoes2" /></div>
          <div><img src="../assets/img/sneakers (2).png" alt="shoes3" /></div>
        </figure>
      </article>
    </section>
    <!-- 11 ~ 19-->
    <section
      v-else-if="
        infoWeather.current?.temp_c >= 11 && infoWeather.current?.temp_c < 19
      "
    >
      <article>
        <h3>Accessories</h3>
        <figure>
          <div><img src="../assets/img/cap.png" alt="accesories1" /></div>
          <div>
            <img src="../assets/img/sunglasses.png" alt="accesories2" />
          </div>
          <div><img src="../assets/img/bucket.png" alt="accesories3" /></div>
        </figure>
      </article>
      <article>
        <h3>Top</h3>
        <figure>
          <div><img src="../assets/img/coat (3).png" alt="top1" /></div>
          <div><img src="../assets/img/cardigan.png" alt="top2" /></div>
          <div>
            <img src="../assets/img/cardigan (1).png" alt="top3t" />
          </div>
        </figure>
      </article>
      <article>
        <h3>Bottoms</h3>
        <figure>
          <div><img src="../assets/img/pants (4).png" alt="bottoms3" /></div>
          <div><img src="../assets/img/pants (3).png" alt="bottoms1" /></div>
          <div><img src="../assets/img/loose-pants.png" alt="bottoms2" /></div>
        </figure>
      </article>
      <article>
        <h3>Shoes</h3>
        <figure>
          <div><img src="../assets/img/sneakers.png" alt="shoes1" /></div>
          <div><img src="../assets/img/sneakers (1).png" alt="shoes2" /></div>
          <div><img src="../assets/img/sneakers (2).png" alt="shoes3" /></div>
        </figure>
      </article>
    </section>
    <!-- 5 ~ 11 -->
    <section
      v-else-if="
        infoWeather.current?.temp_c >= 5 && infoWeather.current?.temp_c < 11
      "
    >
      <article>
        <h3>Accessories</h3>
        <figure>
          <div><img src="../assets/img/beanie.png" alt="accesories1" /></div>
          <div>
            <img src="../assets/img/scarf.png" alt="accesories2" />
          </div>
          <div><img src="../assets/img/socks.png" alt="accesories3" /></div>
        </figure>
      </article>
      <article>
        <h3>Top</h3>
        <figure>
          <div><img src="../assets/img/sweater.png" alt="top1" /></div>
          <div><img src="../assets/img/sweater(1).png" alt="top2" /></div>
          <div>
            <img src="../assets/img/sweater(2).png" alt="top3t" />
          </div>
        </figure>
      </article>
      <article>
        <h3>Bottoms</h3>
        <figure>
          <div><img src="../assets/img/pants (3).png" alt="bottoms1" /></div>
          <div><img src="../assets/img/loose-pants.png" alt="bottoms2" /></div>
          <div><img src="../assets/img/pants (4).png" alt="bottoms3" /></div>
        </figure>
      </article>
      <article>
        <h3>Shoes</h3>
        <figure>
          <div><img src="../assets/img/boots.png" alt="shoes1" /></div>
          <div><img src="../assets/img/boots(1).png" alt="shoes2" /></div>
          <div><img src="../assets/img/boots(2).png" alt="shoes3" /></div>
        </figure>
      </article>
    </section>
    <!-- less than 5 -->
    <section v-else-if="infoWeather.current?.temp_c < 5">
      <article>
        <h3>Accessories</h3>
        <figure>
          <div>
            <img src="../assets/img/winter-hat.png" alt="accesories1" />
          </div>
          <div>
            <img src="../assets/img/glove.png" alt="accesories2" />
          </div>
          <div><img src="../assets/img/earmuffs.png" alt="accesories3" /></div>
        </figure>
      </article>
      <article>
        <h3>Top</h3>
        <figure>
          <div><img src="../assets/img/coat.png" alt="top1" /></div>
          <div><img src="../assets/img/coat (1).png" alt="top2" /></div>
          <div>
            <img src="../assets/img/coat (2).png" alt="top3t" />
          </div>
        </figure>
      </article>
      <article>
        <h3>Bottoms</h3>
        <figure>
          <div><img src="../assets/img/winter.png" alt="bottoms1" /></div>
          <div><img src="../assets/img/winter(1).png" alt="bottoms2" /></div>
          <div><img src="../assets/img/winter(2).png" alt="bottoms3" /></div>
        </figure>
      </article>
      <article>
        <h3>Shoes</h3>
        <figure>
          <div><img src="../assets/img/boots.png" alt="shoes1" /></div>
          <div><img src="../assets/img/boots(1).png" alt="shoes2" /></div>
          <div><img src="../assets/img/boots(2).png" alt="shoes3" /></div>
        </figure>
      </article>
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