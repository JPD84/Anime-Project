<template>
    <div v-if="film">
        <h1>Description</h1>
        <h2>{{film.description}}</h2>
        <ul>
            <li>
                Release date:{{film.release_date}}
            </li>
        </ul>
    </div>
</template>

<script>
// import { eventBus } from "./main.js";
    export default {

        name: "film-detail",
        props: ["film"]    
        
        
    }
</script>

<style scoped>

</style>

