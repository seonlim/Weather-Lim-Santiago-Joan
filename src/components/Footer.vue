<template>
<footer>
    <article>
        <span>
            Weather
        </span>
        <p>
            Experience weather like never before with our nice weather website. Get real-time updates, accurate forecasts, and a user-friendly interface. Discover the perfect blend of simplicity and functionality. 
        </p>
    </article>
    <section>
        <small>
            Copyright &copy; 2023 Weather
        </small>
        <a href="#">
            BACK TO TOP
        </a>
    </section>
</footer>
</template>


<script>
export default {
    name:'Footer', 
    setup(){
        return {

        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:ital,wght@0,300;0,400;0,500;0,700;0,800;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');

* {
  margin: 0;
  padding: 0;
  font-family: "Open Sans", sans-serif;
}

html {
  scroll-behavior: smooth;
}

a {
  text-decoration: none;
}

p {
    line-height: 1.5;
}

footer {
    display: flex;
    flex-direction: column;
    height: 30vh;
    background-color: white;
    color: rgb(69, 114, 159);
    row-gap: 3vh;
    justify-content: center;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}

footer > article {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    width: 100%;
}

footer > section {
    display: flex;
    flex-direction: column;
    align-items: center;
    row-gap: 1vh;

}

footer a,
footer span {
    font-weight: 600;
}

footer p {
    width: 40%;
}

footer a {
    color: rgb(69, 114, 159);

}



</style>