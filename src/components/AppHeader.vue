<script>
import { store } from '../store';
    export default {
     data() {
        return {
            store,
            searchInput: ''

        }
     },
     methods: {
        sendInputsearch(){
            this.$emit("searchField")
        }
    }

    }
</script>

<template>
    <header>

        <div class="container d-flex justify-content-between py-3">
            <div>LOGO</div>

            <div class="groupSearchField">
                <input type="text" v-model="store.searchedInput" placeholder="Inizia la tua ricerca">
                <button type="button" @click="sendInputsearch">Search</button>
            </div>
        </div>        

    </header>
</template>

<style scoped>

header {
    background-color: black;
}

</style>