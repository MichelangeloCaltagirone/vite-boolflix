<script>
import AppMain from './components/AppMain.vue';
import AppHeader from './components/AppHeader.vue';
import axios from 'axios';
import { store } from './store';

    export default {
        data() {
            return {
                apiUrl: 'https://api.themoviedb.org/3/search/movie',
                apiKey: 'c1b93991122e2f217ab436b870ea2f9a',
                query: '',
                store
            }
    },
    components: {
        AppHeader,
        AppMain,
        store
    },
    methods: {
        getSearchField() {
            console.log('evento arrivatto in appVue'),
            console.log(this.store.searchedInput)
        },

        getMoviesList(query) {
            console.log(query)
        },

        getMoviesList(query) {
            axios.get(this.apiUrl, {
                params: {
                    api_key: this.apiKey,
                    query: query
                }
            })
            .then((response) => {
                console.log(response.data.results);
                this.store.moviesList = response.data.results
            })
            .catch(function (error) {
                console.log(error);
            })
        }
    }
    

    }
    
    
</script>

<template>

<AppHeader @searchField="getMoviesList(store.searchedInput)"/>
<AppMain/>

</template>

<style lang="scss">

@use './style/general.scss' as *;
@import '../node_modules/bootstrap/dist/css/bootstrap.css';


</style>
