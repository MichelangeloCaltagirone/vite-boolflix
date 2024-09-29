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
       
        <img v-if="movie.poster_path" :src="this.suorce + this.size + movie.poster_path" :alt="movie.title">
        <div v-else class="substitutePic px-3 d-flex flex-column justify-content">
           <h2 class="text-info fw-bold pt-3">No Poster Pic for:</h2>
           <span class="text-white my-5 fs-5">{{ movie.title }}</span>
           <span class="text-center fs-3">(Hover for more info)</span> 
        </div>
    </div>

    <div class="customBackCard">

        <p class="text-white"><span class="text-success fw-bold">Titolo:</span> {{ movie.title }} </p>
        <p><span class="text-success fw-bold">Titolo Originale:</span> {{ movie.original_title }} </p>
        <p><span class="text-success fw-bold">Lingua:</span> {{ movie.original_language }} </p>
        <p><span class="text-success fw-bold">Voto: </span>
            <span v-for="n in (Math.ceil(movie.vote_average / 2))"><i class="fa-solid fa-star"></i></span>
            <span v-for="n in (5 - Math.ceil(movie.vote_average / 2))"><i class="fa-regular fa-star"></i></span>
        </p>
        <p><span class="text-success fw-bold">Overview: </span>{{ movie.overview }} </p>
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
.substitutePic {
height: 513px;
background-color: black;
}

</style>