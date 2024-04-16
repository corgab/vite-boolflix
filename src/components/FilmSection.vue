<template>
    <div>
        <h2>FILMS</h2>
        <ul>
            <li v-for="film in store.films">
                {{ film.name }}
                {{ film.original_name }}
                <!-- {{ film.original_language }} -->
                <span class="fi" :class="'fi-'+film.original_language"></span>
                {{ convertVote(film.vote_average) }}
                <img :src="`https://image.tmdb.org/t/p/${this.store.widthImg}${film.poster_path}`" alt="">
            </li>
        </ul>
    </div>
</template>

<script>
    import { store } from '../store.js'
    export default {
        data() {
            return {
                store,
            }
        },
        methods: {
            //da mettere globale ma non so farlo
            convertVote(num) {
                // converti il numero ad 1-5
                const fiveVote = Math.round(num / 2)

                //controllare se il numero è tra 1-5
                if(fiveVote < 1) {
                    return 1
                } else if(fiveVote > 5) {
                    return 5
                } else return fiveVote
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>