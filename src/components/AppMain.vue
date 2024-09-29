<script>
import { store } from '../store';
import MainMovieList from './MainMovieList.vue';
import MainSeriesList from './MainSeriesList.vue';



    export default {
        data() {
            return {
                store
            }
        },
        components: {
            MainMovieList,
            MainSeriesList
        }
    }

</script>

<template>
   
   <main>

        <div class="container">

            <h1 class="text-center py-3 text-danger fw-bold">Movie List</h1>

            <div class="list d-flex flex-wrap">                
                <MainMovieList v-for="movie in this.store.moviesList" :key="movie.id" :movie="movie" />
            </div>

            <h1 class="text-center py-3 text-primary fw-bold">TV Series List</h1>

            <div class="list d-flex flex-wrap">                
                <MainSeriesList v-for="series in this.store.tvSeriesList" :key="series.id" :series="series" />
            </div>          

        </div>

   </main>  

</template>

<style scoped>

main {
    background-color: #434343;
    
}

</style>