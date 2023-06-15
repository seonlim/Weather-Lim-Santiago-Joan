<template>
    <section class="container">
        <p>container</p>
    </section>
</template>


<script>
export default {
    name:'CurrentData',
    setup() {
        return {
            api: "/src/services/currentResponse.json",
            weatherData:{}
        }
        
    },
    methods:{
        async getData(){
            try{
                let response = await fetch(this.api);
                 this.weatherData =await response.json().then(data=> data);
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
padding: 10vh;
}
</style>