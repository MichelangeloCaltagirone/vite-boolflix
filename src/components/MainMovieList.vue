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

  <div class="customContainer">

    <div class="customFrontCard">
       
        <img :src="this.suorce + this.size + movie.poster_path" :alt="movie.title">
    </div>

    <div class="customBackCard">

        <p> {{ movie.title }} </p>
        <p> {{ movie.original_title }} </p>
        <p> {{ movie.original_language }} </p>
        <p v-if="movie.vote_average">
            <span v-for="n in (Math.ceil(movie.vote_average / 2))"><i class="fa-solid fa-star"></i></span>
        </p>
        <p> {{ movie.overview }} </p>
    </div>

  </div>
    

</template>

<style scoped>
.customContainer {
    width: 342px;
    height: 513px;
    margin: 3rem auto;

    &:hover {
        .customFrontCard {
            display: none;
        }
        .customBackCard {
            display: block;
        }
    }
}

.customBackCard {
    display: none;
}
img {
    width: 342px;
    height: 513px;
}
.fa-star {
    color:goldenrod
}

</style>