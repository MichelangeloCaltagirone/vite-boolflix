<script>
import { store } from '../store';
    export default {
        data() {
            return {
                suorce: 'https://image.tmdb.org/t/p/',
                size: 'w342'
            }
        },
        props: {
            movie: {
                required: true,
                type: Object
            }
        },
        methods: { 
            getImageUrl(picPath) {
                return new URL(`../assets/img/${picPath}`, import.meta.url).href
            }
        }
    }
</script>

<template>

    <div class="customCard">
        <p> {{ movie.title }} </p>
        <p> {{ movie.original_title }} </p>
        <p> {{ movie.original_language }} </p>
        <p> {{ movie.vote_average }} </p>
        <img :src="this.suorce + this.size + movie.poster_path" :alt="movie.title">
    </div>

</template>

<style scoped>
.customCard {
    flex-basis: 33%;
    padding: 5px 15px;
}

</style>