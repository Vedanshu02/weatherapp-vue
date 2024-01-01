<script lang="ts">
import { defineComponent,ref } from 'vue'
import 'bootstrap/dist/css/bootstrap.css';
import 'bootstrap-vue/dist/bootstrap-vue.css';

//importing show component
import Show from './Show.vue';
export default defineComponent({
   name:'App',
   components:{Show},
   setup(){
    const options = {
    method: "GET",
    headers: {
      "X-RapidAPI-Key": "567c5a9105msh55406b38cf45291p1f80bajsn351bfc2f2ace",
      "X-RapidAPI-Host": "weather-by-api-ninjas.p.rapidapi.com",
    },
  };

     const city= ref("");
     const temperature=ref("");
     const humidity=ref("");
     const data=ref("")
    //API Call For The City That USer Enters
     const searchVal = (name:string)=> {
      fetch("https://weather-by-api-ninjas.p.rapidapi.com/v1/weather?city=" + name,options)
      .then((response) => response.json())
      .then((response) => {
        console.log(response);
           data.value=response;
          })
         
     }
     return {city,searchVal,temperature,humidity,data}
   }
});
</script>

<template>
    <div class="main">

        <h1>Weather of City </h1>

        <div class="container">
          <!-- form for search the city name-->
          <form class="d-flex" role="search">
            <input class="form-control me-2" type="search" placeholder="Enter The City Name" aria-label="Search" v-model="city">
            <button @click.prevent="searchVal(city)" class="btn btn-outline-info" type="submit">Search</button>
          </form> 
        
        <!-- show component with Porps-->
        <Show v-if="data" :data="data" />
        </div>

    </div>
</template>

<style scoped>
.main{ 
    background: url(../assets/background.jpg);
    background-position: center;
    background-size: cover;
    text-align: center;
    height: 92dvh;
}
.d-flex{
margin-top: 20px;
}
</style>