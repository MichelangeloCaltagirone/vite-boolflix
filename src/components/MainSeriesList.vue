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
            series: {
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
       
        <img :src="this.suorce + this.size + series.poster_path" :alt="series.name">
    </div>

    <div class="customBackCard">

        <p> {{ series.name }} </p>
        <p> {{ series.original_name }} </p>
        <p> {{ series.original_language }} </p>
        <p> {{ series.vote_average }} </p>
        <p> {{ series.overview }} </p>
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

</style>