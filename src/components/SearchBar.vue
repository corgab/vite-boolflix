<template>
    <div>
        <input type="text" placeholder="Cerca il tuo Film" v-model="store.query">
        <button @click="getMovie(), getFilm()">Cerca</button>
    </div>
    <div>
        <!-- <ul>
            <li v-for="movie in store.movies">
                {{ movie.title }}
                {{ movie.original_title }}
                {{ film.original_language }}
                <span class="fi" :class="'fi-'+movie.original_language"></span>
                {{ movie.vote_count }}
            </li>
            <li v-for="film in store.films">
                {{ film.name }}
                {{ film.original_name }}
                <span class="fi" :class="'fi-'+film.original_language"></span>
                {{ film.vote_count }}
            </li>
        </ul> -->
    </div>
</template>

<script>
import "/node_modules/flag-icons/css/flag-icons.min.css"
import { store } from '../store.js'
import axios from 'axios'
export default {
    data() {
        return {
            store,
        }
    },
    methods: {
        getMovie() {
            axios.get('https://api.themoviedb.org/3/search/movie', {
                params: {
                    api_key: this.store.API_KEY,
                    query: this.store.query

                }
            })
                .then((res) => {
                    console.log('movies', res.data.results)

                    for (let i = 0; i < res.data.results.length; i++) {
                        const result = res.data.results[i]
                        this.store.movies.push(result)
                    }

                })
        },
        getFilm() {
            axios.get('https://api.themoviedb.org/3/search/tv', {
                params: {
                    api_key: this.store.API_KEY,
                    query: this.store.query

                }
            })
                .then((res) => {
                    console.log('film', res.data.results)

                    for (let i = 0; i < res.data.results.length; i++) {
                        const results = res.data.results[i]
                        this.store.films.push(results)
                    }
                    // console.log(this.films)
                    // console.log(this.films.title)

                })
        },
        // getMovieImg() {
        //     axios.get(`https://image.tmdb.org/t/p/${this.store.widthImg}`)
        //         .then((res) => {
        //             console.log(res)

        //         })
        // },

    },
    // mounted() {
    //     console.log(this.getFilm())
    // }
}

</script>

<style lang="scss" scoped>
// .fi {
//     background-size: contain;
//     background-position: 50%;
//     background-repeat: no-repeat;
// }</style>
