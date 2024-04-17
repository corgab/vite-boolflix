<template>
    <div>
        <h2>FILMS</h2>
        <ul class="flex">
            <li v-for="film in store.films" class="card-margin">
                <div class="card">
                    <img :src="`https://image.tmdb.org/t/p/${this.store.widthImg}${film.poster_path}`" alt="">
                    <div class="card-hover">
                        <h3>Titolo: {{ film.name }}</h3>
                        <h4>Titolo originale:{{ film.original_name }}</h4>
                        <div>
                            <h4>Lingua: {{ film.original_language }} <span class="fi"
                                    :class="'fi-' + film.original_language"></span></h4>
                            <h4>Votazione:
                                <span v-for="star in convertVote(film.vote_average)" class="star">
                                    <font-awesome-icon icon="star" />
                                </span>
                            </h4>

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
        }
    }
}
</script>

<style lang="scss" scoped></style>