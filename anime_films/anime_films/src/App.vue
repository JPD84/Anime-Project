<template>
  <div id="app">
    <h1>Anime Films</h1>
    <film-list v-if="films.length" :films="films"></film-list>
    <film-detail v-if="selectedFilm" :film="selectedFilm"></film-detail>
  </div>
</template>

<script>
import filmList from "./filmList.vue";
import { eventBus } from "./main.js";
import filmDesc from "./filmDesc.vue";


export default {
  name: "app",
  data() {
    return {
      films: [],
      selectedFilm: null
    };
  },
components:{
  "film-list": filmList,
  "film-detail": filmDesc
},

  mounted() {
    fetch("https://ghibliapi.herokuapp.com/films")
    .then (res => res.json())
    .then (films => (this.films = films))
    eventBus.$on("film-selected", film =>{
      this.selectedFilm = film;
    })
    
  }
};
</script>

<style>
</style>
