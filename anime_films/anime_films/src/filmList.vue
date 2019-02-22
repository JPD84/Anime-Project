<template>
    <div>
        <label class="selectLabel" for="filmSelector">Select Film</label>
        <select id="filmSelector" v-model="filmIndex" v-on:change="selectHandler">
        <option v-for="(film, index) in films" :value="index">{{film.title}}</option>
        </select>    

    </div>
</template>

<script>
import { eventBus } from "./main.js";
    export default {
        name: "film-list",
        data(){
            return{
                filmIndex: null,
            };
        },
        
    
    props: ["films"],
   
    methods:{
        selectHandler(){
            eventBus.$emit("film-selected", this.films[this.filmIndex] )
        }
     }
    }


</script>

<style scoped>

</style>