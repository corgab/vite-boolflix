<template>
    <div>
        <h2>MOVIES</h2>
        <ul class="flex">
            <li v-for="movie in store.movies" class="card-margin">
                <div class="card">
                    <img :src="`https://image.tmdb.org/t/p/${this.store.widthImg}${movie.poster_path}`" alt="">
                    <div class="card-hover">
                        <h3>Titolo: {{ movie.title }}</h3>
                        <h4>Titolo originale: {{ movie.original_title }}</h4>
                        <h4>Generi:  
                            <p v-for="id in movie.genre_ids" :key="id"> {{ getGenreName(id) }}</p>
                        </h4>
                        <div>
                            <h4>Lingua: {{ movie.original_language }}
                                <span class="fi" :class="'fi-' + movie.original_language"></span>
                            </h4>
                            <h4>Votazione:
                                <span v-for="star in convertVote(movie.vote_average)" :key="star" class="star">
                                    <font-awesome-icon icon="star" />
                                </span>
                            </h4>
                            <!-- <span v-for="star in convertVote(movie.vote_average)">
                                <font-awesome-icon icon="star" />
                            </span> -->
                        </div>
                    </div>
                </div>

            </li>
        </ul>
    </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faStar } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faStar)

import { store } from '../store.js'
export default {
    data() {
        return {
            store,
        }
    },
    components: {
        FontAwesomeIcon
    },
    methods: {
        //da mettere globale ma non so farlo
        convertVote(num) {
            // converti il numero ad 1-5
            const fiveVote = Math.round(num / 2)

            //controllare se il numero è tra 1-5
            if (fiveVote < 1) {
                return 1
            } else if (fiveVote > 5) {
                return 5
            } else return fiveVote
        },
        getGenreName(id) {
            console.log(this.store.moviesGenres)
            for (let i = 0; i < this.store.moviesGenres.length; i++) {
                // console.log(this.store.moviesGenres[i].id)
                if (this.store.moviesGenres[i].id === id) {
                    return this.store.moviesGenres[i].name
                }
            }
            return 'non conosco';
        },
    }
}
</script>

<style lang="scss" scoped></style>