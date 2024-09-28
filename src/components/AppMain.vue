<script>
import { store } from '../store';
import MainItemList from './MainItemList.vue';


    export default {
        data() {
            return {
                store
            }
        },
        components: {
            MainItemList
        }
    }

</script>

<template>
   
   <main>

        <div class="container">

            <div class="list d-flex flex-wrap">
                <MainItemList v-for="movie in this.store.moviesList" :key="movie.id" :movie="movie" />
            </div>          

        </div>

   </main>  

</template>

<style scoped>

</style>