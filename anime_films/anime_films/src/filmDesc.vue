<template>
    <div class="desc" v-if="film">
        <h2>Description</h2>
        <h2>{{film.description}}</h2>
        <ul>
            <li>
                Release date: {{film.release_date}}
            </li>
            <li>
                RT Score: {{film.rt_score}}
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



