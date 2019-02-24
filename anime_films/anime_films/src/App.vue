<template>

  <div id="app">
    <h1>Anime Films</h1>
    <film-list v-if="films.length" :films="films"></film-list>
    <film-detail v-if="selectedFilm" :film="selectedFilm"></film-detail>
    <film-fav v-if="favouriteFilm" :film="favouriteFilm"></film-fav>
  </div>
  
</template>

<script>
import filmList from "./filmList.vue";
import { eventBus } from "./main.js";
import filmDesc from "./filmDesc.vue";
// import filmFav from "./filmFav.vue";


export default {
  name: "app",
  data() {
    return {
      films: [],
      selectedFilm: null,
      // favouriteFilms:[],
    };
  },
components:{
  "film-list": filmList,
  "film-detail": filmDesc,
  // "film-fav": filmFav,
},

  mounted() {
    fetch("https://ghibliapi.herokuapp.com/films")
    .then (res => res.json())
    .then (films => (this.films = films))
    eventBus.$on("film-selected", film =>{
      this.selectedFilm = film;
    // eventBus.$on("film-fav", film =>{
    //   this.favouriteFilms = film;
    // })
    })
    
  }
};
</script>

<style>


body{
  background-image: url("./animepic2.png");
  background-size: cover;
  background-repeat: no-repeat;

}

#app{
  display:flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-family: 'Doppio One', sans-serif;
  font-size: 20px;
  /* src: url(link href="https://fonts.googleapis.com/css?family=Doppio+One" rel="stylesheet"); */
  /* text-align: center */
};


.desc{
   opacity: 0.6;
   margin: 30px;
   border: 10px solid rgb(40, 10, 148);
   background-color: #ffffff;
   /* filter: alpha(opacity=60); */
}

   /* /* background-color: white!important;
   opacity: 0.65;
   border-color: transparent!important;
  */

.selectLabel{

  font-display: 'Doppio One', sans-serif; 
  font-size: 25px; 
}

/* #filmSelector{
  block-size: 10px;
  font-display: 'Doppio One', sans-serif; 
  width: 500px;
  padding-bottom: 300px;
  -webkit-box-sizing: content-box;
  font-size: 20px; 

} */

.Title{
  font-display: 'Doppio One', sans-serif; 
  font-size: 40px; 

}


</style> 

